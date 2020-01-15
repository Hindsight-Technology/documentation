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
Salary Rules are grouped into categories and organized by sequence.  The sequence is very important because it will indicate the order that the rule will be executed on the Payslip.  

There is a set structure for Salary Rule Sequences:

**EMPLOYEE**

0-98              Wages

99                Gross Wages

100 - 199         Pre tax Additions and Deductions

200 - 299         Taxes Country

300 - 399         Taxes State/Other

400 - 499         

500 - 599         Post Tax Additions and Deductions

600 - 699         

700 - 799         

800 - 899

900 - 998

999               Net 

**COMPANY**

1000 - 1999       Items not taken from Payslip but calculated

1200 - 1299       Company Taxes Federal

1300 - 1399       Company Taxes State/Other

1400 - 1499       Workers Compensation

1500 - 1599       Union Benefits

1600 - 1699

1700 - 1799

1800 - 1899

1900 - 1999


**IMPORTANT!  Remember that if you want to have your salary rules impact the General Ledger that you need to add the Gl acounts on each salary rule.**

Setup Tax Rules
--------------------

Tax calculations are done with a 2 rule combination.  The first rule is the actual tax calculation.

1- Verify that their are Federal and State tax rules created. Each Tax calculation should have a linked Subject To rule. It is important that all tax rules have the following:

- Is Tax = true and the tax application is set to employee or employer tax

- The subject to rule is linked. If there is not an applicable subject to rule created one must be created. The drop down will only show rules that are a part of the Subject to category. If you are going to create a new subject to rule, make sure that it is part of the subject to category.


