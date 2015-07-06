Order Approval extension adds an approval process to the standard ordering workflow in Magento. The approval process is managed by "approvers". An "approver" is any customer with "approver" role enabled.


The approval process sits between customer's shopping cart and the checkout process. Customers can add any number of products to cart, delete and modify them at any time without any restrictions, but they can not checkout products from the cart before they are approved.


When customers try to checkout their shopping cart, the customer's approver receives a notification about unapproved products in the customer's shopping cart. The approver can use links from the e-mail to reach the order approval UI and approve customer's products. Customers can check approval status for every product in their shopping cart and can checkout items that have already been approved.



# Configuration #

The extension requires no special configuration in the system area.

You may want to check the contents of the email templates and add necessary email addresses to the system config area for copies of order emails.

## Setting up approvers ##

An admin can change any user to be an approver by setting _Is approver_ attribute to _Yes_ on customer details page in the admin.

Any other user can be assigned an approver by selecting one from a dropdown on customer details page in the admin. Also approver can be assigned to all users from certain customer group.

## Notification emails ##
The extension sends e-mails on following events:

  * **On checkout** it sends _Items to Approve_ email to the approver
  * **On approve** it sends _Approved Items_ email to a customer and Magento's Custom Email 1 (see _Admin -> System -> Configure -> Store Email Addresses -> Custom Email 1_ tab)
  * **On decline** it sends _Declined Items_ email to a customer

## How to create a custom notification email ##
There's an e-mail template editor in M. admin interface (System -> Transactional Emails). Administrators can create new e-mail templates based on original M. templates.

Step 1: Press Add New Template button. Select one of Order Approval templates such as _Items to Approve_, _Approved Items_ and _Declined Items_. Select a locale you want to use the new template in. Press Load Template button to load content of the template for further editing.

Step 2: Input a name for the new template. Edit its subject and content.
<a href='Hidden comment: 
Note. Input your store URL before {{var customers_shopping_cart_url}} to ensure approvers get a direct link to the approval UI.
'></a>When done, press Save Template button.

Step 3: Select your newly created template on _System -> Configuration -> ZetaPrints Order Approval -> Emails_ tab from a list.

## How to make it work with M. web-to-print extension ##
Both Order Approval and web-to-print extensions support each other out of the box.


# Approval process workflow #
![http://create.ly/gbvkju1s1?a=b.png](http://create.ly/gbvkju1s1?a=b.png)

# Approval status for cart item #
Item's option 'additional\_options' was used to save and show approval status for an item.
These options are displayed in Product name column on shopping cart page.

See '_add\_notice\_to\_approved\_item' method code in [app/code/community/ZetaPrints/OrderApproval/controllers/CartController.php](http://code.google.com/p/magento-w2p/source/browse/branches/ZetaPrints_OrderApproval/app/code/community/ZetaPrints/OrderApproval/controllers/CartController.php) file and code in [app/code/community/ZetaPrints/OrderApproval/controllers/OnepageController.php](https://code.google.com/p/magento-w2p/source/browse/branches/ZetaPrints_OrderApproval/app/code/community/ZetaPrints/OrderApproval/controllers/OnepageController.php) file._



Support code is split into two parts.

One part from the OrderApproval extension checks if a web-to-print helper class exists. If it does exist, then the web-to-print extension has been installed already and OrderApproval extension uses the helper class to display previews from web-to-print orders on approval UI pages.

Another part of support code from web-to-print extension adds resource files (JS and CSS) to approval UI pages in zptheme layout file.

# Total removal of extension #
Magento's ConnectManager doesn't support roll-back of DB changes and removing custom attributes added by the extension. Follow these instructions to completely remove the extension:
  * Remove extension via Magento's ConnectManager
  * Copy [uninstall.php](http://magento-w2p.googlecode.com/svn/branches/ZetaPrints_OrderApproval/uninstall/uninstall.php) file to the root folder of your M. installation.
> Note: change including path at the beginning of the script if you copied it into another directory or a subdirectory of M. installation.

> Examples:
    * If you copied script into 'media/' subdirectory of M. installation then change include path to '../app/Mage.php' in the script.
    * If you copied script into 'media/tmp/' subdirectory (or another subdirectory of 'media/' directory) then change include path to '../../app/Mage.php' in the script.

> In most cases, there are URL re-writes (re-directs) in root directory of M. installation. So, scripts from root directory are not available. The easiest workaround is to copy the script into a directory without re-writes (re-directs), e.g. 'media/' directory and fix include path in the script as described above.

  * Point browser to uninstall.php file from your M. installation
  * Remove the script from your M. installation.

# Added or changed M. files #
The extension adds several files (none are changed) to base theme, such as additional layout and template files to checkout module, some widget templates from admin theme and adds e-mail templates.

List of added files:
  * Files from [app/design/frontend/base/default/layout/checkout/](http://code.google.com/p/magento-w2p/source/browse/#svn/branches/ZetaPrints_OrderApproval/app/design/frontend/base/default/layout/checkout) directory
  * [app/design/frontend/base/default/template/checkout/cart/edit.ptml](http://code.google.com/p/magento-w2p/source/browse/branches/ZetaPrints_OrderApproval/app/design/frontend/base/default/template/checkout/cart/edit.phtml) file
  * Files from [app/design/frontend/base/default/template/checkout/cart/edit/](http://code.google.com/p/magento-w2p/source/browse/#svn/branches/ZetaPrints_OrderApproval/app/design/frontend/base/default/template/checkout/cart/edit) directory
  * Files from [app/design/frontend/base/default/template/widget](http://code.google.com/p/magento-w2p/source/browse/#svn/branches/ZetaPrints_OrderApproval/app/design/frontend/base/default/template/widget) directory
  * [skin/frontend/base/default/css/order-approval/styles.css](http://code.google.com/p/magento-w2p/source/browse/branches/ZetaPrints_OrderApproval/skin/frontend/base/default/css/order-approval/styles.css) file
  * [app/locale/en\_US/template/email/sales/new-items-to-approve.txt](http://code.google.com/p/magento-w2p/source/browse/branches/ZetaPrints_OrderApproval/app/locale/en_US/template/email/sales/new-items-to-approve.txt) file

# Re-defined M. classes #
  * Class Mage\_Checkout\_CartController is re-defined by ZetaPrints\_OrderApproval\_CartController class.
> Re-defined functions:
    * indexAction ()
  * Class Mage\_Checkout\_OnepageController is re-defined by ZetaPrints\_OrderApproval\_OnepageController class
> Re-defined functions:
    * indexAction ()
  * Class Mage\_Checkout\_Block\_Cart is re-defined by ZetaPrints\_OrderApproval\_Block\_Cart class
> Re-defined functions:
    * getItems ()
    * chooseTemplate ()
  * Class Mage\_Checkout\_Model\_Cart is re-defined by ZetaPrints\_OrderApproval\_Model\_Cart
> Re-defined functions:
    * getItems ()
    * getQuoteProductIds ()
    * init ()
    * addProduct ()
    * updateItems ()
    * removeItem ()
    * truncate ()
    * getProductIds ()
  * Class Mage\_Sales\_Model\_Quote is re-defined by ZetaPrints\_OrderApproval\_Model\_Quote
> Re-defined functions:
    * 