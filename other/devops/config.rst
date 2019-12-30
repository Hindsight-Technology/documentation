:banner: banners/development/development.jpg

============================
Configuration File Paramenters
============================

limit_memory_soft
--------------------
Applies per process, in both modes (multi-process and multi-thread). Should be large enough to hold the VM size between requests. It is also used to determine the size of the registry LRU (assuming 15MB per db), so 15 * 80MB should allow you to hold 80 dbs. Some registries may be larger so YMMV, you might want to reserve 30MB per db.

If it's not correctly set it will cause faster worker recycling, and possibly poor perf, but should not block the system.

You do not want to set it higher than server_ram / workers, and probably less than that as you should reserve some amount of memory on the side for the system cache/buffers (and for the DB if your PG server is on the same machine).

On macOS this setting needs to be set exaggeratedly high because the OS allocates 4GB of virtual memory for each process, making it more or less useless as a lim

limit_memory_hard
-------------------

Applies per process, in both modes (multi-process and multi-thread).

Needs to be higher than limit_memory_soft and has to allow for the largest memory footprint you can get in normal operations, including rendering large PDF reports of processing large batches of documents.

If set too low the request will abort immediately, so it can be a showstopper.

As a ballpark figure, 1GB more than limit_memory_soft should be fine, because it allows the request to use 1GB more memory on top of the registry cache, which is not bad. You can have some overcommit here (workers x limit_memory_hard > max_memory_reserved_for_odoo) because not all your workers will be at the max setting all the time.

Same disclaimer for macOS as for limit_memory_soft.

limit_request
----------------
Applies per process, in multi-process mode only. Doesn't matter much, as worker recycling is not more costly than registry and cache invalidations, which happen much more frequently. Also applies to cron worker, which will respawn after waking up limit_request times.
Default is fine but you can increase 2x or 3x if you want, you probably won't see any the difference.

limit_time_cpu
----------------
Only available in multi-process mode (workers>0).
It doesn't matter much in most cases, as the limit_time_real setting will be your main defense against long-running requests. Setting it to 1/3 or 1/2 of the limit_time_real should be fine, as the system does a lot of non-cpu operations (i/o to db, network and filesystem).

db_maxconn
---------------
Max size of the database connection pool.

PostgreSQL's max_connections should be set higher than db_maxpool * number_of_processes. You may need to tweak the kernel sysctl if you need max_connections higher than 1-2k.

For multi-processing mode, each HTTP worker handles a single request at a time, so theoretically db_maxconn=2 could work (some requests need 2 cursors, hence 2 db connections). However for multi-tenant this is not optimal because each request will need to reopen a new connection to a different db - setting it a bit higher is better. With lots of workers, 32 is a good trade-off, as 64 could make you reach kernel limits. Also keep in mind that the limit applies to the longpolling worker too, and you don't want to delay chat messages too much because of a full connection pool, so don't set it too low no matter what. Keeping the value in the 32-64 range usually seems a good choice.

For multi-thread mode, since there is only 1 process, this is the size of the global connection pool. To prevent errors, it should be set between 1x and 2x the expected number of concurrent requests at a time. Can be estimated based on the number of databases and the expected activity. Having a single process handle more than 20 request at a time on a single core (remember that multi-thread depends on the GIL) is unlikely to give good performance, so again, a setting in the 32-64 range will most likely work for a normal load.


number of workers (multi-process mode)
--------------------------------------------
**Disclaimer:** this is for self-hosted multi-process mode. For Odoo.SH a "worker" is actually a multi-threaded task queue, and the numbers are different.

So the documentation states that a single worker can handle 6 users. What it means to say is that a worker can handle on average ~ 6 heavy read transactions / second (150ms each) = 6 web requests/s. If a user triggers about 60 heavy requests / minute during active use, that's 1 req/s on average, so 6 users could max out a worker during peaks, when all of them are active.
But in reality humans don't create sustained load, and the real usage will average out over time to a much lower number, maybe 20% of that, so a single worker may be able to handle dozens of normal users.
Unless you're facing pathological cases, like a class where all students click at the same time, or heavy automated RPC scripts (non-human heavy users), you could start with 1 worker for 30 users, maybe even 40 in a multi-tenant case where the users are distributed on different time zones, and not all databases are active at the same time.

If you don't know how many workers you will need, start with 10 [*], but try to have the flexibility (in RAM and CPU) to deploy more easily as needed. Monitor your system to see how you're doing in terms of resources and transaction rates.

Other things to consider:

Always configure more than 6 workers, as browsers will need to open many parallel connections and you don't want them to be queued, as users will feel the delays. 6 or 8 is a minimum, even if you don't have enough CPUs.
The real limit to the number of workers is the RAM, not the CPUs. If workers x limit_memory_hard is much more than the available RAM, you could cause swapping or crashing. These days get at least 32GB or 64GB RAM, it's not much, and if you don't allocate everything to Odoo, the rest will be useful for OS cache and buffers.
You can go for 2 x num_cpus + 1 workers to make sure you will be using all the cores available. Having less workers than that is a waste of resources. But you can have more workers if you want, as long as you have enough RAM.
CPU speed matters, so try to get the best CPU clock speed you can. Better split the workers on several servers with less CPU cores but higher clocks speeds.
[*] or better yet, do some real load-testing and see how many you actually need to be comfortable!
Reference:
https://github.com/lsegal/atom-rst-preview/blob/master/sample.rst
