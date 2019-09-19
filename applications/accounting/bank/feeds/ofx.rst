:banner: banners/accounting/banking.jpg

=================================
Import OFX or QFX statement files
=================================

Open Financial Exchange (OFX) and Quicken Financial Exchange (QFX) are unified specifications for the
electronic exchange of financial data between financial institutions,
businesses and consumers via the Internet.

With Twenty20, you can download an OFX or a QFX file from your bank or accounting
software and import it directly in your Twenty20 instance. This will create
all bank statements.

.. tip::

	Test now the feature `with this sample OFX file <https://drive.google.com/file/d/0B5BDHVRYo-q5Mmg4T3oxTWszeEk/view>`__

Configuration
=============

In order to import OFX or QFX statements, you need to activate the feature in
Twenty20. In the Accounting application, go to the menu :menuselection:`Configuration -->
Settings`. From the accounting settings, check the bank statements option
**Import in .OFX Format** and apply.

.. image:: media/ofx01.png
   :align: center

Once you have installed this feature, you can setup your bank account to
allow importing bank statement files. To do this, go to the accounting
Dashboard, and click on the **More** button of the bank account.
Then, click on **Import Statement** to load your first OFX or QFX file.

.. image:: media/ofx02.png
   :align: center

Load your OFX or QFX file in the following screen and click **Import** to
create all your bank statements.

.. image:: media/ofx03.png
   :align: center

If the file is successfully loaded, you will get redirected to the bank
reconciliation screen with all the transactions to reconcile.

Importing OFX or QFX files
===================

After having imported your first file, the Twenty20 accounting dashboard
will automatically propose you to import more files for your bank. For
the next import, you don't need to go to the **More** menu anymore,
you can directly click on the link **Import Statement**.

.. image:: media/ofx04.png
   :align: center

Every time you get a statement related to a new customer / vendor,
Twenty20 will ask you to select the right contact to reconcile the
transaction. Twenty20 learns from that operation and will automatically
complete the next payments you get or do to these contacts. This will
speed up a lot the reconciliation process.

.. seealso::

	* :doc:`qif`
	* :doc:`coda`
	* :doc:`synchronize`
	* :doc:`manual`
