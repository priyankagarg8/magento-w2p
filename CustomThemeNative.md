# Introduction #

The web-to-print extension comes with a default theme modified to include all the necessary code from the extension. A Magento website can use a different theme modified to include the code as explained in this manual.

  1. Read this manual
  1. Study the default theme files
  1. Transfer the code from the default theme to your custom theme
  1. Test on w2p and non-w2p products

**Disclaimer**: theme modifications require a certain level of programming skill.

All files listed here can be found in the [extension](http://www.magentocommerce.com/extension/1586) on Magento-Connect or in the [svn repository](http://code.google.com/p/magento-w2p/source/checkout).

Every file has the new code divided into several sections. Every section has its sequence number (e.g. ZP-CODE:1) and is enclosed with comments similar to this:

```
/****** ZP-CODE:1 Short description of code in the block ******/

some code

/****** ZP-CODE:1 End ******/
```

# Personalization form #
The form is a modified product details page. You need to insert certain function calls at places where the blocks of HTML should show. This screenshot is only a guide to how it can be laid out on the screen. The functions are described below in the article.
![http://www.zetaprints.com/magento-docs/theme-configuration.png](http://www.zetaprints.com/magento-docs/theme-configuration.png)

# Custom theme requirements #

The web-to-print extension has several requirements to HTML code of the custom theme.

  * _app/design/frontend/default/`<`your\_custom\_theme\_name`>`/template/catalog/product/view.phtml_
> Set **id** attribute of preview image container (can be a parent, but not immediate one) to **zetaprints-preview-image-container** value. Search for _ZP-CHANGE:1_ string in [view.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/catalog/product/view.phtml) file from _zptheme_ theme for example.
  * _app/design/frontend/default/`<`your\_custom\_theme`>`/template/catalog/product/view/media.phtml_
> Set **id** attribute of product image tag to **image** value. Search for _ZP-CHANGE:1_ string in [media.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/catalog/product/view/media.phtml) file from _zptheme_ theme for example

# Files in `app/design/frontend/default/<your_theme_name>/` #

You need to modify some files behind the user interface.

## [template/catalog/product/view.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/catalog/product/view.phtml) ##
This file shows form for ordering on product page. This form contains product images, product name, product description, product price, etc.

New code checks for web-to-print features in a product and adds additional options (ajax image preview, colour picker, stock images chooser and support for multipage templates).

The code is divided into 6 sections.

**Section 1**: output image tabs for multi-page products with web-to-print feature
```
<?php $this->helper('webtoprint/personalization-form')->get_page_tabs($this); ?>
```

**Section 2 (optional)**: output button for showing data sets. Add the function if you need this feature.
```
<?php $this->helper('webtoprint/personalization-form')->getDataSetTable($this); ?>
```

**Section 3**: output input fields, images, stock images, colour pickers and palettes for products with web-to-print feature
```
<?php $this->helper('webtoprint/personalization-form')->get_text_fields($this); ?>
<?php $this->helper('webtoprint/personalization-form')->get_image_fields($this); ?>
<?php echo $this->getChildHtml('webtoprint_palettes'); ?>
```

**Section 4**: output web-to-print buttons for products with web-to-print feature
```
<?php echo $this->getChildHtml('webtoprint_buttons'); ?>
```

**Section 5**: output JavaScript for the personalisation form
```
<?php $this->helper('webtoprint/personalization-form')->get_js($this); ?>
```

**Optional section**: output a table with page sizes for products with web-to-print feature. Add the function if you need this feature.
```
<?php $this->helper('webtoprint/personalization-form')->getPageSizeTable($this); ?>
```

The function supports inches and centimetre units. Set second parameter of the function as 'in' to display page size in inches or 'cm' to display in centimetres.
By default (as in example above) it uses inches to display page size.

Example:
```
//Display page sizes in centimetres.
<?php $this->helper('webtoprint/personalization-form')->getPageSizeTable($this, 'cm'); ?>
```

## [template/catalog/product/view/addto.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/catalog/product/view/addto.phtml) ##
This file needs to be modified only if you want to show _Share preview_ link so that users can grab the URL of the image and share it with someone else. In this case the image is downloaded from ZP to your Magento site for keeping (ZP deletes unused images quickly). The download happens asynchronously when the user clicks on the sharing text box.

Preview downloading is initiated only then user clicks on text input with URL. All previews downloaded from ZetaPrints are saved in _media/tmp/catalog/product/previews/_ directory. The directory is created automatically during the extension installation process. Old preview images need to be removed manually from the temp directory.

The following ZP code adds link to show text field with sharing url for a generated preview. You can insert this function into any other place in the layout, which may be in a different file.

**Section 1**: add preview sharing link
```
<?php $this->helper('webtoprint/personalization-form')->get_preview_image_sharing_link(); ?>
```

## [template/catalog/product/view/media.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/catalog/product/view/media.phtml) ##
This file shows product image, additional images and image zoomer on product page.

New code checks for web-to-print in a product and puts correct images urls additional images.

**Section 1**: remove web-to-print images from the gallery on personalisation form
```
<?php $this->helper('webtoprint/personalization-form')->prepare_gallery_images($this) ?>
```

## [template/checkout/cart/item/default.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/checkout/cart/item/default.phtml) ##
This file shows various information for cart item on shopping cart page.

New code checks for web-to-print in a product and puts correct images urls for cart item,
also it adds link to PDF proofs.

**Section 1**: output link and slightly modified <img> tag with correct image url, add link to PDF proof for the template and returns true for products with web-to-print features<br>
<pre><code>&lt;?php if(!$this-&gt;helper('webtoprint/personalization-form')-&gt;get_cart_image($this)): ?&gt;<br>
</code></pre>

<h2><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/sales/order/items.phtml'>template/sales/order/items.phtml</a></h2>
This file show various information for order item on user orders page.<br>
<br>
New code checks for web-to-print in a product and shows preview images for order items.<br>
<br>
<b>Section 1</b>: insert link to hide/show all previews<br>
<pre><code>&lt;?php echo $this-&gt;helper('webtoprint/personalization-form')-&gt;show_hide_all_order_previews($this); ?&gt;<br>
</code></pre>

<b>Section 2</b>: insert preview images from the order for web-to-print products<br>
<pre><code>&lt;?php $this-&gt;helper('webtoprint/personalization-form')-&gt;get_order_preview_images($this, $_item); ?&gt;<br>
</code></pre>

<b>Section 3</b>: inserting javascript code for previews images<br>
<pre><code>&lt;?php $this-&gt;helper('webtoprint/personalization-form')-&gt;get_js_for_order_preview_images($this); ?&gt;<br>
</code></pre>

<h2><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/sales/order/items/renderer/default.phtml'>template/sales/order/items/renderer/default.phtml</a></h2>
This file shows various information for particular order item on user orders page.<br>
<br>
The following ZP code shows links to generated output files (PDF/PNG/JPG/GIF) in order details. The links appear if the files were generated and the template config (in ZP) has <i>download by customer</i> setting set to either <i>allow</i> (a user can download files) or <i>only</i> (the order is for downloading only, nothing gets printed). The function returns nothing if the conditions above are not met.<br>
<br>
<b>Section 1</b>: output links to web-to-print generated files<br>
<pre><code>&lt;?php echo $this-&gt;helper('webtoprint/personalization-form')-&gt;get_order_webtoprint_links($this, $_item); ?&gt;<br>
</code></pre>

The following ZP code adds re-order link to an order item. After clicking on the link the corresponding product page will be opened and fields from personalization form will be filled with values from the order.<br>
<br>
<b>Section 2</b>: output link for re-ordering<br>
<pre><code>&lt;?php echo $this-&gt;helper('webtoprint/personalization-form')-&gt;get_reorder_button($this, $_item); ?&gt;<br>
</code></pre>

<h2><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zptheme/template/wishlist/item/column/image.phtml'>template/wishlist/item/column/image.phtml</a></h2>
This file shows images for products on <i>wishlist</i> page.<br>
<br>
New code checks for web-to-print in the product, puts correct image urls for the whislist item and adds links to PDF proofs.<br>
<br>
Second and third parameters of the helper function are width and height of the image.<br>
Choose values according your custom theme.<br>
<br>
<b>Section 1</b>: output link and slightly modified <img> tag with correct image url, add link to PDF proof for the template and returns true for products with web-to-print features<br>
<pre><code>&lt;?php if(!$this-&gt;helper('webtoprint/personalization-form')-&gt;get_cart_image($this, 113, 113)): ?&gt;<br>
</code></pre>

<h1>Functions</h1>
Most of the extension code is encapsulated in functions. The functions make all necessary checks of the context and return values only if needed. E.g. <code>get_text_fields ($context)</code> function returns nothing if the product has no web-to-print features. This way they do not affect products that have nothing to do with web-to-print.<br>
<br>
<ul><li><code> get_product_image ($context, $product)</code> - Outputs nothing, always returns <i>false</i>. (<b>Deprecated</b>)<br>
</li><li><code> get_page_tabs ($context)</code> - outputs image tabs for multipage templates<br>
</li><li><code> get_text_fields ($context)</code> - outputs text fields for products with web-to-print features<br>
</li><li><code> get_image_fields ($context)</code> - outputs image fields (stock images, color picker) for products with web-to-print features<br>
</li><li><code> get_preview_button ($context)</code> - outputs <i>Update preview</i> button for products with web-to-print features<br>
</li><li><code> get_js ($context)</code> - outputs javascript code for products with web-to-print features<br>
</li><li><code> get_js_css_includes ($context)</code> - Outputs nothing, always returns <i>false</i>. (<b>Deprecated</b>)<br>
</li><li><code> get_preview_images ($context)</code> - Outputs nothing, always returns <i>false</i>. (<b>Deprecated</b>)<br>
</li><li><code> get_gallery_thumb ($context, $product, $image)</code> - Outputs nothing, always returns <i>false</i>. (<b>Deprecated</b>)<br>
</li><li><code> get_gallery_image ($context)</code> - Outputs nothing, always returns <i>false</i>. (<b>Deprecated</b>)<br>
</li><li><code> get_cart_image ($context, $width = 0, $height = )</code> - outputs a slightly modified <code>&lt;img&gt;</code> tag to prevent image resizing with the correct image url and returns <i>true</i> for products with web-to-print features<br>
</li><li><code> get_order_preview_images ($context)</code> - outputs previews images for order.<br>
</li><li><code> get_reorder_button ($context, $item)</code> - outputs A tag with link to re-order web-to-print product page.<br>
</li><li><code> getPageSizeTable ($this, $units = 'in')</code> - displays table with template's page sizes.</li></ul>

<h1>Adjust size for different images (preview, stock and user images)</h1>
Preview are generated by [www.zetaprints.com www.zetaprints.com] at a certain default size. Magento can reduce the preview size, but cannot make it larger. If the preview provided by zetaprints.com is not large enough you need to <a href='http://www.zetaprints.com/help/changing-default-previews/'>generate a bigger one first</a>.<br>
<br>
<br>
Size of <b>preview images</b> can be changed in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/skin/frontend/base/default/css/zp-style.css'>zp-style.css</a></i> file, see <i>a.zetaprints-template-preview img</i> CSS selector.<br>
<br>
<pre><code>a.zetaprints-template-preview img {<br>
  max-width: 265px;<br>
  ...<br>
}<br>
</code></pre>


Size of <b>stock images</b> in a library scroll can be changed in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/skin/frontend/base/default/css/zp-style.css'>zp-style.css</a></i> file for PNG and GIF and in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/Zpapi/Model/common-templates.xslt'>common-templates.xslt</a></i> file for other supported image types. By default every stock image is scaled down to 100px in height.<br>
<br>
<ul><li><b>PNG and GIF images</b>
</li></ul><blockquote>Change <i>max-width</i> attribute in <i>div.images-scroller img</i> CSS selector in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/skin/frontend/base/default/css/zp-style.css'>zp-style.css</a></i> file.<br>
<pre><code>div.images-scroller img {<br>
  ...<br>
  max-height: 100px;<br>
  ...<br>
}<br>
</code></pre></blockquote>

<ul><li><b>Other supported image types</b>
</li></ul><blockquote>Change <i>0x100</i> part of image URL to preferred one where template is <i>WEIGHTxHEIGHT</i> (in pixels) in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/Zpapi/Model/common-templates.xslt'>common-templates.xslt</a></i> file.<br>
<pre><code>&lt;xsl:otherwise&gt;<br>
  &lt;img src="{$zetaprints-api-url}photothumbs/{substring-before(@Thumb,'.')}_0x100.{substring-after(@Thumb,'.')}" /&gt;<br>
&lt;/xsl:otherwise&gt;<br>
</code></pre></blockquote>

Size of <b>user images</b> in library scroll can be changed in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/skin/frontend/base/default/css/zp-style.css'>zp-style.css</a></i> file for PNG and GIF and in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Helper/PersonalizationForm.php'>PersonalizationForm.php</a></i> (for already uploaded images) and <a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/controllers/UploadController.php'>UploadController.php</a> (for newly uploaded images) files for other supported image types. By default every user image is scaled down to 100px in height.<br>
<br>
<ul><li><b>PNG and GIF images</b>
</li></ul><blockquote>Same as for PNG or GIF stock images.</blockquote>

<ul><li><b>Other supported image types</b>
</li></ul><blockquote>Change <i>0x100</i> value of parameter to preferred one where template is <i>WEIGHTxHEIGHT</i> (in pixels) in <i><a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Helper/PersonalizationForm.php'>PersonalizationForm.php</a></i> and <a href='http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/controllers/UploadController.php'>UploadController.php</a> files.<br>
<pre><code>if ($image['mime'] === 'image/jpeg' || $image['mime'] === 'image/jpg')<br>
  $thumbnail = str_replace('.', '_0x100.', $image['thumbnail']);<br>
</code></pre></blockquote>

<h1>Spinners for progress of AJAX requests</h1>
There's two types of spinners: big and normal. Big spinner is used for preview loading progress. Normal spinner is used for different AJAX requests to M.<br>
<br>
<ul><li>Image for big spinner is <a href='http://magento-w2p.googlecode.com/svn/trunk/skin/frontend/base/default/images/big-spinner.gif'>skin/frontend/base/default/images/big-spinner.gif</a>
</li><li>Image for normal spinner is <a href='http://magento-w2p.googlecode.com/svn/trunk/skin/frontend/base/default/images/spinner.gif'>skin/frontend/base/default/images/spinner.gif</a></li></ul>

<h1>Styling links added by the extension</h1>
Here is list of CSS class name selectors for links added by the extension:<br>
<ul><li>Product page:<br>
<ul><li><code>.add-to-links span.zetaprints-share-link a</code> - selector for "Share preview" link<br>
</li><li><code>.add-to-links span.zetaprints-share-link.empty a</code> - selector for "Share preview" link in disabled state<br>
</li></ul></li><li>Shopping cart page:<br>
<ul><li><code>a.zetaprints-lowres-pdf-link</code> - selector for "PDF Proof" link<br>
</li></ul></li><li>Order details page:<br>
<ul><li><code>a.zetaprints-reorder-item-link</code> - selector for "Reorder" link<br>
</li><li><code>a.zetaprints-order-file-link</code> - selector for web-to-print order files<br>
</li></ul><blockquote>Links to different types (i.e. PDF, PNG, GIF, JPEG, CDR) of web-to-print order files can be distinguished by additional class name (same as file type). E.g. <code>a.zetaprints-order-file-link.pdf</code> - selector for PDF web-to-print order files.<br>
</blockquote><ul><li><code>a.all-order-previews</code> - selector for "Show all order previews" and "Hide all order previews"<br>
</li><li><code>div.zetaprints-previews-box a.show-title</code> - selector for "Show previews" links<br>
</li><li><code>div.zetaprints-previews-box a.hide-title</code> - selector for "Hide previews" links</li></ul></li></ul>

<h1>Fake Add to cart button</h1>
The extension hides original Add to cart button to prevent adding not personalized products to a customer's cart. Absence of original button may produce a bad user-experience in some cases. So, fake Add to cart button is added to leave store interface consistent.<br>
<br>
Use following CSS selectors to style fake Add to cart button and text notice under it:<br>
<ul><li><code>#zetaprints-fake-add-to-cart-button</code> - for the button<br>
</li><li><code>#zetaprints-fake-add-to-cart-warning</code> - for the notice</li></ul>

<h1>NOSCRIPT</h1>
Product personalisation form requires JavaScript. The form won't load fully if JS is disabled. Make sure your theme has <code>&lt;NOSCRIPT&gt;</code> area to warn customers about the requirement in a visible and informative way.<br>
<br>
<br>
<a href='http://www.zetaprints.com/magento-web-to-print/magento-partners'><img src='http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png' /></a>