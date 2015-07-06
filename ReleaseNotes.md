# Stable release (2.4.0.0) #
  * Add support for RWD-based themes
  * Other small bug fixes and improvements

## Release comments ##
**NOTE:** if you're using custom theme (not based on RWD theme), please, enable support for it. Go to _Admin interface_ -> _System_ -> _Configuration_ -> _ZetaPrints Web-to-print_ tab -> _Theme Compatibility_ section -> _Enable support for old custom themes_ setting and then select your theme in the list of themes.

Code for the release can be obtained by _web-to-print-2.4.0.0_ tag from the project's SVN repo.

# Stable release (2.3.0.1) #
  * Fix regression which made assigning web-to-print template to product in product editor broken

## Release comments ##
**NOTE:** this release doesn't support new RWD theme out of the box

Code for the release can be obtained by _web-to-print-2.3.0.1_ tag from the project's SVN repo.

# Stable release (2.3.0.0) #
  * Synchronise with Magento 1.9.0.2
  * Remove support for Magento releases older than 1.6
  * Improvements in 2-step theme
  * Other small bug fixes and improvements

## Release comments ##
**NOTE:** this release doesn't support new RWD theme out of the box

Code for the release can be obtained by _web-to-print-2.3.0.0_ tag from the project's SVN repo.


# Stable release (2.2.0.0) #
  * Synchronise with Magento 1.8.0.0 and 1.8.1.0 versions
  * Add support for quantities in ZetaPrints templates (needs documentation)
  * Add support for colour palettes in ZetaPrints templates
  * Add support for storing w2p product (previews and user input) in wishlist ([issue #823](https://code.google.com/p/magento-w2p/issues/detail?id=#823))
  * Allow to use dummy store for category name mapping (needs documentation)
  * Add parameter to enable assigning of created product to parent categories in profile for product creation (needs documentation)
  * Add an option to select websites for assiging of newly created products (needs documentation)
  * Re-assigned product to category on update (needs documentation)
  * Show warning when user changed data in fields but has not updated previews yet
  * Other small bug fixes and improvements

## Release comments ##
Code for the release can be obtained by _web-to-print-2.2.0.0_ tag from the project's SVN repo.

# Stable release (2.1.6.0) #
  * Fix several bugs in Dataset feature ([issue #820](https://code.google.com/p/magento-w2p/issues/detail?id=#820))
  * Fix error with pre-filled w2p fields on product page ([issue #821](https://code.google.com/p/magento-w2p/issues/detail?id=#821))

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.6.0_ tag from the project's SVN repo.

# Stable release (2.1.5.0) #
  * Fix error in getting link of preview image for sharing
  * Fix removing Magento's zoomer on personalisation step in 2-step theme
  * Fix reordering functionality ([issue #815](https://code.google.com/p/magento-w2p/issues/detail?id=#815))
  * Update jQuery to 1.8.3 and jQuery UI to 1.8.24
  * Update JS code to work correctly with jQuery 1.8
  * Other small bug fixes and improvements

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.5.0_ tag from the project's SVN repo.

# Stable release (2.1.4.1) #
  * Fix error when image was selected in every field after uploading it.

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.4.1_ tag from the project's SVN repo.

# Stable release (2.1.4.0) #
  * Fix the case when API code doesn't send data to the Zetaprints ([issue #808](https://code.google.com/p/magento-w2p/issues/detail?id=#808))

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.4.0_ tag from the project's SVN repo.

# Stable release (2.1.3.0) #
  * Restore removed user on ZetaPrints side ([issue #804](https://code.google.com/p/magento-w2p/issues/detail?id=#804))

# Stable release (2.1.2.0) #
  * Add support for Magento 1.7
  * Add Dutch translation ([issue #788](https://code.google.com/p/magento-w2p/issues/detail?id=#788))
  * Display preview images in order's notification emails ([issue #798](https://code.google.com/p/magento-w2p/issues/detail?id=#798))
  * Do not ignore empty lines in drop-down text fields([issue #795](https://code.google.com/p/magento-w2p/issues/detail?id=#795))
  * Better handling of template's previews ([issue #797](https://code.google.com/p/magento-w2p/issues/detail?id=#797))
  * Other bug fixes and improvements ([issue #772](https://code.google.com/p/magento-w2p/issues/detail?id=#772), [issue #794](https://code.google.com/p/magento-w2p/issues/detail?id=#794), [issue 797](https://code.google.com/p/magento-w2p/issues/detail?id=797), [issue #749](https://code.google.com/p/magento-w2p/issues/detail?id=#749))

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.2.0_ tag from the project's SVN repo.

# Stable release (2.1.1.0) #
  * Add default ZetaPrints account settings ([issue #770](https://code.google.com/p/magento-w2p/issues/detail?id=#770))
  * Bug fixes and improvements ([issue #773](https://code.google.com/p/magento-w2p/issues/detail?id=#773), [issue #774](https://code.google.com/p/magento-w2p/issues/detail?id=#774) and [issue #776](https://code.google.com/p/magento-w2p/issues/detail?id=#776))

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.1.0_ tag from the project's SVN repo.

# Stable release (2.1.0.0) #
## Issues ##
  * Re-implement data sets ([issue #737](https://code.google.com/p/magento-w2p/issues/detail?id=#737))
  * Add option to ignore unpaid orders ([issue #738](https://code.google.com/p/magento-w2p/issues/detail?id=#738))
  * Add support for PayPal Express Checkout ([issue #744](https://code.google.com/p/magento-w2p/issues/detail?id=#744))
  * Add link to finalise order on ZP in admin interface ([issue #739](https://code.google.com/p/magento-w2p/issues/detail?id=#739))
  * Implement new form buttons ([issue #652](https://code.google.com/p/magento-w2p/issues/detail?id=#652))
  * Implement fallback scenario to preserver user's input ([issue #539](https://code.google.com/p/magento-w2p/issues/detail?id=#539))
  * Complete ZP order on Processing status ([issue #750](https://code.google.com/p/magento-w2p/issues/detail?id=#750))
  * Bug fixes ([issue #725](https://code.google.com/p/magento-w2p/issues/detail?id=#725))

## Release comments ##
Code for the release can be obtained by _web-to-print-2.1.0.0_ tag from the project's SVN repo.

# Stable release (2.0.0.1) #
## Issues ##
  * Add support for M. 1.6.1.0 ([issue #678](https://code.google.com/p/magento-w2p/issues/detail?id=#678))
  * Add support for dynamic imaging ([issue #654](https://code.google.com/p/magento-w2p/issues/detail?id=#654))
  * Add support for shopping cart items editing ([issue #701](https://code.google.com/p/magento-w2p/issues/detail?id=#701))
  * Fit-in-field ([issue #660](https://code.google.com/p/magento-w2p/issues/detail?id=#660), [issue #662](https://code.google.com/p/magento-w2p/issues/detail?id=#662), [issue #666](https://code.google.com/p/magento-w2p/issues/detail?id=#666) and [issue #682](https://code.google.com/p/magento-w2p/issues/detail?id=#682))
  * Add save button for image edit ([issue #663](https://code.google.com/p/magento-w2p/issues/detail?id=#663) and [issue #664](https://code.google.com/p/magento-w2p/issues/detail?id=#664))
  * Add option to set default image library state ([issue #700](https://code.google.com/p/magento-w2p/issues/detail?id=#700))
  * Initial support for datasets ([issue #669](https://code.google.com/p/magento-w2p/issues/detail?id=#669))
  * Add support for optional pages ([issue #688](https://code.google.com/p/magento-w2p/issues/detail?id=#688))
  * Bug fixes and improvements ([issue #653](https://code.google.com/p/magento-w2p/issues/detail?id=#653), [issue #657](https://code.google.com/p/magento-w2p/issues/detail?id=#657), [issue #644](https://code.google.com/p/magento-w2p/issues/detail?id=#644), [issue #665](https://code.google.com/p/magento-w2p/issues/detail?id=#665), [issue #692](https://code.google.com/p/magento-w2p/issues/detail?id=#692), [issue #649](https://code.google.com/p/magento-w2p/issues/detail?id=#649), [issue #717](https://code.google.com/p/magento-w2p/issues/detail?id=#717) and [issue #676](https://code.google.com/p/magento-w2p/issues/detail?id=#676))

## Release comments ##
Code for the release can be obtained by _web-to-print-2.0.0.1_ tag from the project's SVN repo.


# Stable release (1.9.1.1) #
## Issues ##
  * Bug fixes ([issue #641](https://code.google.com/p/magento-w2p/issues/detail?id=#641) and [issue #642](https://code.google.com/p/magento-w2p/issues/detail?id=#642))

# Stable release (1.9.1.0) #
## Issues ##
  * Add Update preview button to the Fancybox pop-up ([issue #541](https://code.google.com/p/magento-w2p/issues/detail?id=#541))
  * Add table with page sizes to a product page ([issue #513](https://code.google.com/p/magento-w2p/issues/detail?id=#513))
  * Add combobox for text fields ([issue #557](https://code.google.com/p/magento-w2p/issues/detail?id=#557))
  * Add support for overlapping fields to in-preview field editor ([issue #564](https://code.google.com/p/magento-w2p/issues/detail?id=#564))
  * Add support for shape with multiple fields ([issue #593](https://code.google.com/p/magento-w2p/issues/detail?id=#593))
  * Add text field's meta data editor to in-preview field editor ([issue #584](https://code.google.com/p/magento-w2p/issues/detail?id=#584))
  * Add default product creation option in admin interface ([issue #589](https://code.google.com/p/magento-w2p/issues/detail?id=#589))
  * Add support for story attribute of text fields ([issue #587](https://code.google.com/p/magento-w2p/issues/detail?id=#587))
  * Add a profile for catalogues creation ([issue #502](https://code.google.com/p/magento-w2p/issues/detail?id=#502))
  * Add Use image button to stock images viewer ([issue #617](https://code.google.com/p/magento-w2p/issues/detail?id=#617))
  * Update jQuery to 1.5.2 release and jQuery UI to 1.8.13 release
  * Bug fixes and improvements ([issue #566](https://code.google.com/p/magento-w2p/issues/detail?id=#566), [issue #548](https://code.google.com/p/magento-w2p/issues/detail?id=#548), [issue #569](https://code.google.com/p/magento-w2p/issues/detail?id=#569), [issue 565](https://code.google.com/p/magento-w2p/issues/detail?id=565), [issue 580](https://code.google.com/p/magento-w2p/issues/detail?id=580), [issue 581](https://code.google.com/p/magento-w2p/issues/detail?id=581), [issue 577](https://code.google.com/p/magento-w2p/issues/detail?id=577), [issue #591](https://code.google.com/p/magento-w2p/issues/detail?id=#591), [issue #603](https://code.google.com/p/magento-w2p/issues/detail?id=#603), [issue #606](https://code.google.com/p/magento-w2p/issues/detail?id=#606), [issue #614](https://code.google.com/p/magento-w2p/issues/detail?id=#614), [issue 623](https://code.google.com/p/magento-w2p/issues/detail?id=623), [issue #628](https://code.google.com/p/magento-w2p/issues/detail?id=#628) and [issue #586](https://code.google.com/p/magento-w2p/issues/detail?id=#586))

## Release comments ##
Code for the release can be obtained by _web-to-print-1.9.1.0_ tag from project's SVN repo.

# Stable release (1.9.0.0) #
## Issues ##
  * Add support for M. 1.5 ([issue #458](https://code.google.com/p/magento-w2p/issues/detail?id=#458))
  * New fit-to-field feature in image editor dialog (disabled by default because of development state)
  * Add ability to choose color for text fields ([issue #375](https://code.google.com/p/magento-w2p/issues/detail?id=#375))
  * Update jQuery to 1.4.4 release and jQuery UI to 1.8.7 release
  * Add support for custom options in separate XML file ([issue #259](https://code.google.com/p/magento-w2p/issues/detail?id=#259))
  * Fancybox resizing capabilities ([issue #251](https://code.google.com/p/magento-w2p/issues/detail?id=#251))
  * Add Spain, Bulgarian, German and Makedonian localizations
  * Implement fake Add to cart button ([issue #374](https://code.google.com/p/magento-w2p/issues/detail?id=#374))
  * Hide Update button on static pages ([issue #273](https://code.google.com/p/magento-w2p/issues/detail?id=#273))
  * Add support for creation of virtual products ([issue #478](https://code.google.com/p/magento-w2p/issues/detail?id=#478))
  * Add support for translation of template's titles, hints and field names ([issue #479](https://code.google.com/p/magento-w2p/issues/detail?id=#479))
  * Implement custom option to allow users download files regardless of ZP template setting ([issue #491](https://code.google.com/p/magento-w2p/issues/detail?id=#491))
  * Bug fixes and improvements ([issue #440](https://code.google.com/p/magento-w2p/issues/detail?id=#440), [issue #436](https://code.google.com/p/magento-w2p/issues/detail?id=#436), [issue #437](https://code.google.com/p/magento-w2p/issues/detail?id=#437), [issue #450](https://code.google.com/p/magento-w2p/issues/detail?id=#450), [issue #188](https://code.google.com/p/magento-w2p/issues/detail?id=#188), [issue #292](https://code.google.com/p/magento-w2p/issues/detail?id=#292), [issue #179](https://code.google.com/p/magento-w2p/issues/detail?id=#179), [issue #483](https://code.google.com/p/magento-w2p/issues/detail?id=#483), [issue #469](https://code.google.com/p/magento-w2p/issues/detail?id=#469), [issue #438](https://code.google.com/p/magento-w2p/issues/detail?id=#438), [issue #489](https://code.google.com/p/magento-w2p/issues/detail?id=#489) and [issue #88](https://code.google.com/p/magento-w2p/issues/detail?id=#88))

## Release comments ##
It's recommended to un-install previous versions of the extension firstly.

**NOTE: Please, remember (write down) your API Key and URL. You have to re-enter them in the extension settings after update**

Please, do following step if you don't use _zptheme_ as default in Magento (e.i. if you previously copied everything from zptheme into the custom theme):

  * **Remove all previously copied files from your custom theme!**
  * Remove layout/local.xml file or leave only custom theme specific changes there
  * Move any changes you made in copied files to proper files from the custom theme.
  * Try **NOT TO OVERRIDE** theme files from the extension. It will make your further updates easier.

# Stable release (1.8.3.2) #
## Issues ##
  * Add support for M. 1.4.2.0 release ([issue #382](https://code.google.com/p/magento-w2p/issues/detail?id=#382))

## Release comments ##
Code for the release can be obtained by _web-to-print-1.8.3.2_ tag from project's SVN repo.

# Stable release (1.8.3.1) #
## Issues ##
  * Bug fixes ([issue #339](https://code.google.com/p/magento-w2p/issues/detail?id=#339), [issue #337](https://code.google.com/p/magento-w2p/issues/detail?id=#337), [issue #334](https://code.google.com/p/magento-w2p/issues/detail?id=#334) and [issue #322](https://code.google.com/p/magento-w2p/issues/detail?id=#322))

# Stable release (1.8.3.0) #
## Issues ##
  * Point product links in cart to already personalized products ([issue #277](https://code.google.com/p/magento-w2p/issues/detail?id=#277))
  * Show arrows in fancybox all the time ([issue #276](https://code.google.com/p/magento-w2p/issues/detail?id=#276))
  * Make all spinners in same color in zptheme ([issue #255](https://code.google.com/p/magento-w2p/issues/detail?id=#255))
  * Memory consumption and speed improvements in product creation profile ([issue #283](https://code.google.com/p/magento-w2p/issues/detail?id=#283))
  * Add support for ZetaPrints OrderApproval extension
  * Update jQuery UI library to 1.8.5 release
  * Bug fixes ([issue #252](https://code.google.com/p/magento-w2p/issues/detail?id=#252), [issue #278](https://code.google.com/p/magento-w2p/issues/detail?id=#278))

## Release comments ##
Please, do following step if you don't use zptheme as default in Magento (e.i. if you copied everything from zptheme into the custom theme):
  * Copy [skin/frontend/default/zptheme/images/spinner.gif](http://magento-w2p.googlecode.com/svn/trunk/skin/frontend/default/zptheme/images/spinner.gif) file into your custom theme's image directory
  * Copy [skin/frontend/default/zptheme/js/jquery-ui-1.8.5-custom-min.js](http://magento-w2p.googlecode.com/svn/trunk/skin/frontend/default/zptheme/js/jquery-ui-1.8.5-custom-min.js) file  into your custom theme's js directory and remove 'jquery-ui-1.8.custom.min.js' file from it.

# Stable release (1.8.2.4) #
  * Bug fixes ([issue #270](https://code.google.com/p/magento-w2p/issues/detail?id=#270), [issue #262](https://code.google.com/p/magento-w2p/issues/detail?id=#262))

# Stable release (1.8.2.3) #
  * Fix bug in product's images update ([issue #274](https://code.google.com/p/magento-w2p/issues/detail?id=#274))

# Stable release (1.8.2.2) #
  * Fix regression in session handling (introduced in 1.8.2.0)

# Stable release (1.8.2.1) #
  * Fix regression in preview share link functionality (introduced in 1.8.2.0)

# Stable release (1.8.2.0) #
## Issues ##
  * Loading indicator for preview images on product page ([Issue #202](https://code.google.com/p/magento-w2p/issues/detail?id=#202))
  * Show up-sell product with prepared preview ([Issue #222](https://code.google.com/p/magento-w2p/issues/detail?id=#222))
  * Add product link to each order item for quick re-ordering ([Issue #216](https://code.google.com/p/magento-w2p/issues/detail?id=#216))
  * Add "Default" option to image fields ([Issue #240](https://code.google.com/p/magento-w2p/issues/detail?id=#240))
  * Add link to ZetaPrints order to every M. order item in admin interface ([Issue #152](https://code.google.com/p/magento-w2p/issues/detail?id=#152))
  * Other improvements ([Issue #221](https://code.google.com/p/magento-w2p/issues/detail?id=#221), [Issue #225](https://code.google.com/p/magento-w2p/issues/detail?id=#225), [Issue #238](https://code.google.com/p/magento-w2p/issues/detail?id=#238)) and little bug fixes.

## Release comments ##
### Quick re-ordering ###
Modify _sales/order/items/renderer/default.phtml_ template file in your custom theme as described in CustomThemeNative page to enable quick re-ordering feature.

### Preview sharing link ###
Modify _catalog/product/view/addto.phtml_ template file in your custom theme as described in CustomThemeNative page to enable preview sharing link functionality.

Please, do following steps if you don't use zptheme as default in Magento (e.i. if you copied everything from zptheme into your custom theme):
  * Add a new loading indicator to your custom theme (_skin/frontend/default/zptheme/images/big-spinner.gif_).
  * Update _zp-style.css_ file in your custom theme (_skin/frontend/default/zptheme/css/zp-style.css_)
> See [changes](http://code.google.com/p/magento-w2p/source/diff?old=811&r=893&format=side&path=%2Ftrunk%2Fskin%2Ffrontend%2Fdefault%2Fzptheme%2Fcss%2Fzp-style.css) for the file in this release if you changed _zp-style.css_ file or included it in your custom theme's CSS file.
  * Update _zp-personalization-form.js_ file in your custom theme (_skin/frontend/default/zptheme/js/zp-personalization-form.js_)
> See [changes](http://code.google.com/p/magento-w2p/source/diff?old=819&r=907&format=side&path=%2Ftrunk%2Fskin%2Ffrontend%2Fdefault%2Fzptheme%2Fjs%2Fzp-personalization-form.js) for the file in this release if you changed _zp-personalization-form.js_ file.
  * Update _zp-in-preview-edit.js_ file in your custom theme (_skin/frontend/default/zptheme/js/zp-in-preview-edit.js_)
> See [changes](https://code.google.com/p/magento-w2p/source/diff?old=789&r=883&format=side&path=%2Ftrunk%2Fskin%2Ffrontend%2Fdefault%2Fzptheme%2Fjs%2Fzp-in-preview-edit.js) for the file in this release if you changed _zp-in-preview-edit.js_ file.

# Stable release (1.8.1.0) #
## Issues ##
  * User image deletion ([Issue #164](https://code.google.com/p/magento-w2p/issues/detail?id=#164))
  * Fix error with product's base image ([Issue #141](https://code.google.com/p/magento-w2p/issues/detail?id=#141))
  * Automatic update of ZetaPrints order status ([Issue #10](https://code.google.com/p/magento-w2p/issues/detail?id=#10))
  * Switch to jQuery 1.4 ([Issue #159](https://code.google.com/p/magento-w2p/issues/detail?id=#159))
  * New theme for in-preview editing ([Issue #177](https://code.google.com/p/magento-w2p/issues/detail?id=#177))
  * Fields highlighting and in-preview fields edit ([Issue #169](https://code.google.com/p/magento-w2p/issues/detail?id=#169), [Issue #170](https://code.google.com/p/magento-w2p/issues/detail?id=#170), [Issue #193](https://code.google.com/p/magento-w2p/issues/detail?id=#193))
  * Better support for HTTPS ([Issue #192](https://code.google.com/p/magento-w2p/issues/detail?id=#192))
  * Order output files download for users ([Issue #198](https://code.google.com/p/magento-w2p/issues/detail?id=#198))
  * Preview image sharing ([Issue #210](https://code.google.com/p/magento-w2p/issues/detail?id=#210))
  * PDF proofs for saved orders ([Issue #191](https://code.google.com/p/magento-w2p/issues/detail?id=#191))
  * Other bug fixes: [issue #163](https://code.google.com/p/magento-w2p/issues/detail?id=#163), [issue #167](https://code.google.com/p/magento-w2p/issues/detail?id=#167), [issue #186](https://code.google.com/p/magento-w2p/issues/detail?id=#186), [issue #207](https://code.google.com/p/magento-w2p/issues/detail?id=#207)

## Release comments ##
Themes running on the previous stable version need to be modified. Themes running on a recent beta release can be left as is. See more info at Custom theme requirements on CustomThemeNative page.

Deprecated functions:
  * _get\_js\_css\_includes()_ ([app/code/local/ZetaPrints/WebToPrint/Helper/PersonalizationForm.php](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Helper/PersonalizationForm.php)) - the function was deprecated because of new way JavaScript and CSS files are included. Follow these steps to update your custom theme:
    1. Copy _app/design/frontend/default/zptheme/layout/local.xml_ file to your custom theme's _layout_ directory or copy its content into _local.xml_ file, if you already have one.
    1. Remove _app/design/frontend/default/your\_custom\_theme\_name/template/page/html/head.phtml_ file from your custom theme. If you did any custom changes to the file then you should remove following line from it:
```
<?php $this->helper('webtoprint/personalization-form')->get_js_css_includes(); ?>
```

  * _get\_admin\_js\_css\_includes()_ ([app/code/local/ZetaPrints/WebToPrint/Helper/PersonalizationForm.php](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Helper/PersonalizationForm.php)) - the function was deprecated because of new way JavaScript and CSS files are included in ZP admin theme. Magento doesn't support any un-installation facilities for its extensions. You should remove _app/design/adminhtml/default/zptheme/template/page/head.phtml_ file manually.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)