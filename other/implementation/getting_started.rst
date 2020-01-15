:banner: banners/development/implementation.jpg

=================================
Getting Started
=================================

New customer Instance
=======================

1- Log on to github - twenty20 repository

2- Click on the drop down "branch" and type in the customer name that will be used. This will create a new blank customer system without any Twenty20 modules installed.

3- Once built, access the customer database manager and delete the existing Db and restore the "New Customer" database.


Setting up new Customer
==========================
1- Log on to the new customer Db and make sure that all necessary modules are installed
    ** HINT**  do a search for t20 and verify that the necessary modules are installed.

2- Setup the new customer company - or have them do it


Quickbook Migration
==========================

Set up
--------

Here are the steps to migrate quickbooks to Twenty20.

**IMPORTANT**  the migration only works for Quickbooks online. If the customer is not using Quickbbooks online, they you will need to restore the QB backup to your quickbooks desktop version as Admin and then convert that file to Quickbooks online

1- Create a clean Database on your local machine

2- Install t20_connect_quickbooks

3- In order to connect your local Twenty20 Database with quickbooks onlien you will need to authenticate with the Twenty20 Connect application in the Quickbooks appstore.  Then you will need to complete the Quickbooks configuration in the Twenty20 Company settings.

    a. Redirect URL: https://developer.intuit.com/v2/OAuth2Playground/RedirectUrl


4- Click "Authenticate" you will be redirected to a OAuth2.0 Playground.  This is the setup for the connection

    a.  Step 1: Get an authorization code. Slect the Twenty20 Connect (Production)

        1) Add the client id and secret to the Twenty20 Company Settings

        2) in OAuth Settings: click "Accounting" checkbox and click "get Authorization code"

    b. You will be redirected to a screen that will connect Twenty20 to your quickboks online account. Click "Connect"

    c. Back in the Playground...

        1) You will need to get the company number and append that you the URL of the API URL.

    d. Click refresh token and the new token details should populate


Import Quickbooks Data
------------------------

1- Follow the step in the import tab to get the Quickbooks data
