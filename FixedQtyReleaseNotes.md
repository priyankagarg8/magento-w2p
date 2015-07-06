# Version 0.9.0b #

## New beta ##
  * added uninstal/uninstall.php to allow for complete removal of extension modifications
  * changed sort order
  * restricted FQ to simple, virtual, downloadable, configurable products only
  * added product names to export file
  * prevented product loading when checking if product uses FQ

# Version 0.5.5b #

## New beta version ##
  * Fixed behavior with product options, now total price is updated by multiplying options price by QTY selected [issue #537](https://code.google.com/p/magento-w2p/issues/detail?id=#537)
  * product options price labels update when new QTY is selected [issue #537](https://code.google.com/p/magento-w2p/issues/detail?id=#537)
  * FQ tab removed for grouped and bundle products [issue #546](https://code.google.com/p/magento-w2p/issues/detail?id=#546)

# Version 0.5.1 #

  * Support for configurable products
  * added check to see if product actually has FQ before required option is used [issue #457](https://code.google.com/p/magento-w2p/issues/detail?id=#457)
  * cart qty box is disabled but not hidden
  * Changes to account for taxes.Also overall handling of FQ is changed a bit. [issue #477](https://code.google.com/p/magento-w2p/issues/detail?id=#477)
  * Change to use new location of fixedprices.phtml file
