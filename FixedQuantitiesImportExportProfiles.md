# Introduction #

Fixed Quantities data should be included into import/export.
A user with large inventory base won't be able to use this extension without off-line editing.

# Details #

Default import/export adapters are not suitable for our type of data.
We have separate adapters specific for FQ only.

Importing fixed quantities has to be done **after** importing base product import.

Each product can have multiple and variable number of FQ. Each
FQ consists of several fields - website, label, qty, price. There fore row format is as follows:

"sku","qty0","label0","price0","default0","qty1","label1","price1","default1","qty2","label2","price2","default2"

Where **sku** is product sku as set in product settings, **qty#** is number of items that are part of the FQ, **label#** is the description text that will be shown before each option, **price#** is the price for the FQ, **default#** is a flag that indicates if this option should be selected as product page is shown to customer.
**#** is number of the FQ, it is not vital to have sequential numbers as long as they are different for each FQ.

File used for import/export should be in .csv format and should use default magento settings - fields enclosed in " (double quotes) and delimited by , (comma).
Something to watch out for is not to have " in label field or if you must have it, escape it with \ (backslash)

Since each product can have arbitrary number of Fixed Quantities assigned you will need to create enough column headings to suit for the greatest number of FQ imported.

Easiest way to edit csv files is to open them in spreadsheet program - Excel, OpenOffice. How to open a csv file in different programs is not related to this topic and is program specific.

There are 2 profiles that handle task of importing/exporting. They can be found in Magento admin section under System > Import/Export > Advanced Profiles (until 1.5) or Dataflow - Advanced Profiles (afetr 1.5)

Profiles are called **ZetaPrints Fixed Quantities Export** and **ZetaPrints Fixed Quantities Import**.

Export profile will save results in **/var/export/fixed\_qtys\_data.csv** by default. Import profile will look for file  **/var/import/fixed\_qtys\_data.csv** by default.
The paths can be changed in admin by altering profile's xml, this however requires good knowledge of how profiles work.