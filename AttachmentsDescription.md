# Introduction #

**Attachments** is Magento extension that allows asynchronous file uploading in product page.


# Details #

## Problems to solve ##
  1. Allow uploading multiple files per 1 custom product option in Magento.
  1. Upload files as you go, asynchronously using queue to avoid hi stress on internet bandwidth.
  1. Display list of uploaded files on every page where quote/order details are shown.
  1. In frontend show the list in plain text format (no links to download files)
  1. In admin order details page, display links to uploaded files so that admin user can download and use files.

## How are problems solved ##

  * Added to Magento is new custom option type 'attachment'.
  * Currently it overrides existing type 'file'.
  * Also added is product attribute 'use\_ajax\_upload' which is enabled/disabled type of attribute. When it is enabled, all attachment features are on, when disabled, the option functions as 'file'.
  * Added single template file catalog/product/view/options/type/attachments.phtml which partially repeats file.phtml content, but instead of directly displaying file upload widget it uses attachments/upload helper.
  * to implement asynchronous part a script called attachments.js is used. All functionality in it is implemented using Prototype framework http://www.prototypejs.org/api , this decision was made for some reasons, but most important is that Magento uses Prototype by default for its JS functionality so no new dependences are introduced.
  * Displaying part of extension is done via extending and overriding some of Magento classes.
    * Mage\_Catalog\_Model\_Product\_Option is overridden by ZetaPrints\_Attachments\_Model\_Product\_Option
    * Mage\_Catalog\_Model\_Product\_Option\_Type\_File is extended from ZetaPrints\_Attachments\_Model\_Product\_Option\_Type\_Attachments
  * Since whole operation is asynchronous we cannot use usual methods for adding custom option to quote, so this is handled via Magento event system and ZetaPrints\_Attachments\_Model\_Events\_Observer

## Usage ##

Admin user adds or edits a product that can use one or more customer files, such as visual templates, fonts, Photoshop brushes etc.



To provide this admin adds custom option from product editing page.

![http://lh3.ggpht.com/_FUsMOYf2KgU/TQIxeESUg-I/AAAAAAAAAHE/jkKNsNyAsbw/admin_product_custom_option.png](http://lh3.ggpht.com/_FUsMOYf2KgU/TQIxeESUg-I/AAAAAAAAAHE/jkKNsNyAsbw/admin_product_custom_option.png)

Admin can choose as many file upload options as needed. For example, graphic designs, fonts, pdf files etc.

Each chosen option will present separate widget that allows queuing multiple files for that option.

To enable AJAX upload admin has to set 'Use AJAX upload' to 'Yes' in general product attributes.

![http://lh6.ggpht.com/_FUsMOYf2KgU/TQIxeBlfUUI/AAAAAAAAAHA/gFFm_mgNut8/admin_product_attribute_use_ajax.png](http://lh6.ggpht.com/_FUsMOYf2KgU/TQIxeBlfUUI/AAAAAAAAAHA/gFFm_mgNut8/admin_product_attribute_use_ajax.png)

By default Magento disallows uploading of .php and .exe files.

A product with this option added, presents to user JavaScript powered file upload widget with looks consistent among major browsers.

![http://lh5.ggpht.com/_FUsMOYf2KgU/TQIxlWrNNjI/AAAAAAAAAHY/wd434HaoyA4/s800/Test_Product_With_Ajax_Upload.png](http://lh5.ggpht.com/_FUsMOYf2KgU/TQIxlWrNNjI/AAAAAAAAAHY/wd434HaoyA4/s800/Test_Product_With_Ajax_Upload.png)

Below each widget there is a reminder of maximum possible file size.

Uploading first file chosen for each option group starts immediately and each additional file is added to queue.

Next to each uploading file is presented a 'cancel' button, that allows the customer to stop the upload if needed.

![http://lh3.ggpht.com/_FUsMOYf2KgU/TQIxldFr0HI/AAAAAAAAAHU/Qq3doU5LFSE/s800/file_loading.png](http://lh3.ggpht.com/_FUsMOYf2KgU/TQIxldFr0HI/AAAAAAAAAHU/Qq3doU5LFSE/s800/file_loading.png)

Upon canceling upload of a file, next in queue starts upload. Canceled file is removed from queue and if customer wants to re - add it , has to choose it again.

Next to each queued file there is a 'remove' link which removes the file from queue. Clicking on that link will remove the file and its form from queue.

In case that user selects the same file more than once it will be uploaded to server
but it will not be saved more than once (no additional disk space will be taken).
Unfortunately JavaScript does not allow to get full file name and path on user
computer. So for example **C:\images\big\image1.jpg** and **C:\images\thumbnails\image1.jpg** are probably different sizes of same picture but when uploading them browser only sees **image1.jpg** and has no way to tell for sure if it is the same file or not. There is no  way with only **JavaScript** to prevent repeating uploads. So the responsibility of which files to upload and keep goes to the user and then to admin of the store.

Magento does not store files with their names. It creates an md5 hash out of file content and uses it as base file name and adds file extension. It then puts the file into custom folder path made out of 2 folders which are named after first 2 letters of original file name. So file **image.jpg** will be saved in relative path **/i/m/ujhfljdslkuwihf784ri432.jpg** This means that if a user uploads same file in 2 separate products or orders, the file will be saved over any previous upload of the same file. This preserves space on disk but also means that if file is physically deleted it will be deleted for all resources that refer to it (all orders or attachment records).

After file is uploaded it has a delete button displayed next to it (same as remove btn), by clicking on it, the file will not be added to order process. This will not however physically delete the file.

During upload, all 'Add to cart' buttons of original Magento form are hidden from client to prevent accidental leaving of the page and by doing this canceling all pending and running uploads. If customer decides that he does not want to upload remaining files, he/she can cancel or remove them and 'Add to cart' buttons will be available again.

After product has been added to cart, all uploaded files are listed in shopping cart, and then in checkout page. Upon order placing if customer is registered, she can see the list of uploaded files in order details page too.

In frontend of Magento files are not available for download, to prevent bandwidth over usage.

![http://lh5.ggpht.com/_FUsMOYf2KgU/TQIxeFo2iTI/AAAAAAAAAHI/KARyFPXE-zQ/s800/file_in_cart.png](http://lh5.ggpht.com/_FUsMOYf2KgU/TQIxeFo2iTI/AAAAAAAAAHI/KARyFPXE-zQ/s800/file_in_cart.png)

![http://lh5.ggpht.com/_FUsMOYf2KgU/TQIxecZ9k6I/AAAAAAAAAHM/0B2fg5AG_Ns/s800/file_in_checkout.png](http://lh5.ggpht.com/_FUsMOYf2KgU/TQIxecZ9k6I/AAAAAAAAAHM/0B2fg5AG_Ns/s800/file_in_checkout.png)

![http://lh3.ggpht.com/_FUsMOYf2KgU/TQIxlJOYXFI/AAAAAAAAAHQ/O7g-dmSyXpU/s800/file_in_order.png](http://lh3.ggpht.com/_FUsMOYf2KgU/TQIxlJOYXFI/AAAAAAAAAHQ/O7g-dmSyXpU/s800/file_in_order.png)

When examining the order in Admin - users are presented with download links to all files attached to order.

![http://lh4.ggpht.com/_FUsMOYf2KgU/TQIxdw0673I/AAAAAAAAAG8/Ywf8PNB7dgw/admin_order_view.png](http://lh4.ggpht.com/_FUsMOYf2KgU/TQIxdw0673I/AAAAAAAAAG8/Ywf8PNB7dgw/admin_order_view.png)


In latest versions, an admin management interface is made to help deleting old and unneeded file from file system. This is implemented as a dedicated menu item in admin backend of Magento. The menu has 2 entries - 'Manage attachments' and 'Attachment settings'.

First entry lists all uploaded files in a table that has options to delete individual files, selected number of files, all orphaned files (files that are not part of an order) and all old files (what is considered 'old' file is set in settings).

Second entry leads to System Configuration tab for Attachments settings. There you can set number of days after which a file is considered 'old'. There are 2 options - **Orphaned files** and **Old files**. Orphaned are any files that did not end up as part of an  order. Old files are all uploaded files including those that are part of an order. If you set any of the options to 0 (zero) it will be skipped. The most logical way of setting those options is to set orphaned days to be less than old days. That will leave files that are used in an order untouched and available for reorder. If you want not to delete order files at all, set old files days to 0.
If you want to delete all files regardless of being part of an order or not at the same time, set orphaned to 0 and old days to what ever number of days you want.