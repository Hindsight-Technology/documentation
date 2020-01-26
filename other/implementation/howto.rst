:banner: banners/development/implementation.jpg

========================
How To's
========================

Update Vendors for 1099
------------------------

1- step 1
To set all Vendor Tax Names to the same as the Vendor Name, you can run this script, *** BUT DO NOT use it if you do not want to overwrite any existing entries in this field!***:
Script: update res_partner set ven_tax_name=name where supplier=True;

2- Step 2
You may have to use the mass edit feature to set Vendor Payments to 'is_1099'
