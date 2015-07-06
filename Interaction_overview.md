# Interaction overview #

This extension does the following:
  * maintains Magento products in sync with ZetaPrints products
  * registers new users in ZetaPrints
  * grants / denies user access to products in ZetaPrints
  * requests final order generation from ZetaPrints
  * downloads order details from ZetaPrints
  * updates order status in ZetaPrints

We need a Use Case diagram here.

# Personalization form #
A product linked to a ZP template throw its _webtoprint\_template_ attribute shows a personalization form on the product details page. See instructions on integrating the form into a theme for [one step proc](http://code.google.com/p/magento-w2p/wiki/CustomThemeNative) and [2 step proc](http://code.google.com/p/magento-w2p/wiki/CustomTheme2Step).

![http://www.zetaprints.com/magento-docs/create-personalization-form.png](http://www.zetaprints.com/magento-docs/create-personalization-form.png)
![http://www.zetaprints.com/magento-docs/create-personalization-form-2step-theme.png](http://www.zetaprints.com/magento-docs/create-personalization-form-2step-theme.png)

Changes since 1.8.2.0:
  1. A user is not registered on ZetaPrints until there is a request for preview generation.
  1. Template details come from M. database for unregistered users on ZetaPrints.
  1. Template details come from ZP directly for registered users and contain user cache.

# Products #

## Dynamic products overview ##
By default a product in Magento has no personalization capabilities. A product can be assigned to a template in its settings in admin area (see _Web-to-print templates_ tab in settings) . Such products can be personalized. Products can be created by the extension using _ZetaPrints products creation_ Advanced Import/Export Profile in M.

## High-level overview of a product personalizing process ##

![http://www.zetaprints.com/magento-docs/generate-preview.png](http://www.zetaprints.com/magento-docs/generate-preview.png)

# Users #
ZetaPrints does not require full user registration to use the services. It only needs a user ID/password combo for data caching and resource allocation. The extension creates a user in ZetaPrints (with generated user ID and password) for every user in M. that uses web-to-print features. See http://www.zetaprints.com/help/user-registration-api

![http://www.zetaprints.com/magento-docs/create-new-zp-user-or-load-existing-one.png](http://www.zetaprints.com/magento-docs/create-new-zp-user-or-load-existing-one.png)

Lifetime of a user session on ZP can be months or even years. The extension stores ZP credentials separate from M. user sessions to restore them later, independently from the M. user session. See a page about UserManagement.

## User access control ##
This extension instructs ZP to grant/deny users access to certain catalogs via API (http://www.zetaprints.com/help/user-access-api/)

# Orders #
Order information is synced between ZetaPrints and M. through this extension.
Zetaprints is only concerned with the image and file generation part of the order. It produces the final product M. sells to the user.

![http://www.zetaprints.com/magento-docs/order-generation.png](http://www.zetaprints.com/magento-docs/order-generation.png)

## Shop owner order management ##
Shop owners have printer accounts with ZP and can login to ZP directly to manage orders. They do not see user details, pricing, payments or any other info held within M.
Normally, orders would be managed through M. Faulty orders may need functions available only within ZP.

## User order management ##
Users registered via M cannot login to ZP and cannot access their order history there.
They need to use M for that.

# Uploading user images #

![http://www.zetaprints.com/magento-docs/upload-user-image.png](http://www.zetaprints.com/magento-docs/upload-user-image.png)

_**Pre-created directory**_ is directory that created after extension installation automatically. Name for the directory is randomly generated GUID (see _zetaprints\_generate\_guid()_ function in _[zp\_api.php](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/Zpapi/Model/zp_api.php)_ file) and saved in M. global config under _zetaprints/webtoprint/uploading/dir_ key. Newly created directory is placed in _media/tmp/catalog/product/_ directory of M. distribution.

The directory must be available throw the web to allow ZetaPrints service download images uploaded by user in M. interface.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)