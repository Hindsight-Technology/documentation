:banner: banners/accounting.jpg

================================
From Vendor Invoices to Payments
================================

Once vendor invoices are registered in Twenty20, you can easily pay vendors for
the correct amount and at the right time (not too late, not too early;
depending on your vendor policy). Twenty20 also offers reports to track your
aged payable balances.

If you want to control vendor invoices received from your vendors, you can
use the Twenty20 Purchase application that allows you to control and
pre-complete them automatically based on past purchase orders.

From Vendor Invoice to Payment
==============================

Record a new vendor invoice
---------------------------

When a vendor invoice is received, you can record it from :menuselection:`Purchases --> Vendor Invoices`
in the Accounting application. As a shortcut,
you can also use the **New Invoice** feature on the accounting dashboard.

.. image:: ./media/vendor_bill05.png
   :align: center

To register a new vendor invoice, start by selecting a vendor and inputting
their invoice as the **Vendor Reference**, then add and confirm the product
lines, making sure to have the right product quantities, taxes and
prices.

.. image:: ./media/vendor_bill01.png
   :align: center

Save the invoice to update the pre tax and tax amounts at the bottom of
the screen. You will most likely need to configure the prices of your
products without taxes as Twenty20 will compute the tax for you.

.. note:: 
    On the bottom left corner, Twenty20 shows a summary table of all taxes on the vendor invoice.
    In several countries, different methods are accepted to round the totals (round per line, 
    or round globally). The default rounding method in Twenty20 is to round the final prices
    per line (as you may have different taxes per product. E.g. Alcohol and cigarettes). 
    However if your vendor has a different tax amount on their invoice, you can change the
    amount in the bottom left table to adjust and match.

Validate The Vendor Invoice
---------------------------

Once the vendor invoice is validated, a journal entry will be generated
based on the configuration on the invoice. This journal entry may differ
depending on the the accounting package you choose to use.

For most European countries, the journal entry will use the following
accounts:

-  **Accounts Payable:** defined on the vendor form

-  **Taxes:** defined on the products and per line

-  **Expenses:** defined on the line item product used

For Anglo-Saxon (US) accounting, the journal entry will use the
following accounts:

-  **Accounts Payable:** defined on the vendor form

-  **Taxes:** defined on the products and per line

-  **Goods Received:** defined on the product form

You can check your Profit & Loss or the Balance Sheet reports after
having validated a couple of vendor invoices to see the impact on your
general ledger.

Pay a invoice
-------------

To create a payment for an open vendor invoice directly, you can click on **Register a
Payment** at the top of the form.

From there, you select the payment method (i.e. Checking account, credit
card, check, etc…) and the amount you wish to pay. By default, Twenty20 will
propose the entire remaining balance on the invoice for payment. In the
memo field, we recommend you set the vendor invoice number as a
reference (Twenty20 will auto fill this field from the from the vendor invoice
if set it correctly).

.. image:: ./media/vendor_bill06.png
   :align: center


.. note::
    You can also register a payment to a vendor directly without applying it to a vendor invoice.
    To do that, :menuselection:`Purchases --> Payments`. Then, 
    from the vendor invoice you will be able to reconcile this payment with directly.

Printing vendor Checks
----------------------

If you choose to pay your vendor invoices by check, Twenty20 offers a method to
do so directly from your vendor payments within Twenty20. Whether you do so
on a daily basis or prefer to do so at the end of the week, you can
print in checks in batches.

If you have checks to print, Twenty20's accounting dashboard acts as a to do
list and reminds you of how many checks you have left to be printed.

.. image:: ./media/vendor_bill02.png
   :align: center

By selecting the amount of checks to be printed, you can dive right into
a list of all payments that are ready to be processed.

Select all the checks you wish to print (use the first checkbox to
select them all) and set the action to **Print Checks**. Twenty20 will ask you
to set the next check number in the sequence and will then print all the
checks at once.

.. image:: ./media/vendor_bill03.png
   :align: center

Reporting
=========

Aged payable balance
--------------------

In order to get a list of open vendor invoices and their related due dates,
you can use the **Aged Payable** report, under the reporting menu, (in
:menuselection:`Reporting --> Business Statement --> Aged payable`) to get a visual of all of
your outstanding invoices.

.. image:: ./media/vendor_bill04.png
   :align: center

From here, you can click directly on a vendors name to open up the
details of all outstanding invoices and the amounts due, or you can
annotate any line for managements information. At any point in time
while you're looking through the report, you can print directly to Excel
or PDF and get exactly what you see on the screen.

.. seealso::
    * :doc:`customer_invoice`