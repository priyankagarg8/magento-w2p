Status of an order on ZP updates to _deleted_ after status of relative M. order changes to _Canceled_ or _Complete_.

Process steps:
  1. Check for M. order status. It should be _Canceled_ or _Complete_.
  1. For every web-to-print item from the order change its status on ZP to _deleted_

Code is placed in _delete\_zetaprints\_order_ function in [app/code/local/ZetaPrints/WebToPrint/Model/Events/Observer.php](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Model/Events/Observer.php) file. The function is registered in M. as a handler for _sales\_order\_save\_after_ event (see [app/code/local/ZetaPrints/WebToPrint/etc/config.xml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/etc/config.xml) file)

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)