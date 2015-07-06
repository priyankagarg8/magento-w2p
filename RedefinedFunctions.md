# Introduction #

This page lists functions from Magento Core re-defined by the extension. It is possible that some other extension will try to re-define them as well leading to conflicts.


# Class _Mage\_Sales\_Model\_Quote\_Item_ #
The class is redefined by **[ZetaPrints\_WebToPrint\_Model\_Quote\_Item](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Model/Quote/Item.php)** class.

Redefined functions:
  * `representProduct ($product)` - If product has web-to-print features then return false to force creating new quote item in cart for personalized product.
  * `compare ($item)` - If quote item represents product with web-to-print features then do not allow merge items in checkout.

# Class _Mage\_Adminhtml\_Block\_Catalog\_Product\_Edit\_Tabs_ #
The class is redifined by **[ZetaPrints\_WebToPrint\_Block\_Catalog\_Product\_Edit\_Tabs](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Block/Catalog/Product/Edit/Tabs.php)** class.

Redefined functions:
  * `_prepareLayout ()` - Add "Web-to-print templates" tab on product configuration page.

# Class _Mage\_Page\_Block\_Html\_Footer_ #
The class is redefined by **[ZetaPrints\_WebToPrint\_Block\_Html\_Footer](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Block/Html/Footer.php)** class.

Redifined functions:
  * `getCopyright ()` - Add version of web-to-print extension.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)