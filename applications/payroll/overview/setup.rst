:banner: banners/payroll/overview.jpg

================
Payroll Setup
================

General Outline
----------------

1- Create a payroll payable account in the General Ledger (type = payable)

2- :ref:`Create all employes <accounting/adviser/assets_management/defining>`. that will be on payroll

.. _accounting/adviser/assets_management/defining:


3- Relate employees to the company

4- Set the company accounting defaults

- Payable account should be the payroll account

5- Create/Edit the payment method and mode for ACH

6- Create applicable salary rules & Inputs

7- Associate rules to the structure

8- Create employee contracts

- Set as hourly or salary

- Set structure

- Set pay schedule

- Add any pay defaults

- Set if direct deposit

- Create direct deposit bank accounts and mode


If customer is going to create invoices for the employee 0 they need to be aware that the invoice will by default have
the Payroll payable account associated to it.

Create and setup new employee
---------------------------------
1-  Open the menu :menuselection:`Human Resources --> Payroll`, then click on the
**Employees** button.


.. image:: ./media/payslip.png
   :align: center

Create employee contracts
-----------------------------

Setup Salary Rules
---------------------

**IMPORTANT!  Remember that if you want to have your salary rules impac the General Ledger that you need to add the Gl acounts on each salary rule.**

Setup Tax Rules
--------------------

Tax calculations are done with a 2 rule combination.  The first rule is the actual tax calculation.

1- Verify that their are Federal and State tax rules created. Each Tax calculation should have a linked Subject To rule. It is important that all tax rules have the following:

- Is Tax = true and the tax application is set to employee or employer tax

- The subject to rule is linked. If there is not an applicable subject to rule created one must be created. The drop down will only show rules that are a part of the Subject to category. If you are going to create a new subject to rule, make sure that it is part of the subject to category.


