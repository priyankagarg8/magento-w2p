# Introduction #

Normal products have a one step process: the product details page contains all the product options and the user adds it to cart on the same page.

Products with personalization can be sold in one step or two step process.
One step: all the options, including the personalization form appear on the same page.
Two step: the user chooses options and then proceeds to the personalization form.

The two step process uses additional functions from ZetaPrints extension. This document explains how the theme should be constructed.

# Two step process overview #

Both steps (options, personalization) use the same page. The code in the theme must make a choice which part of the page to show, depending on the context. Also, the second step should capture and retain all the parameters submitted from the first step.

## Implementation steps ##
  1. Redirect _Add to cart_ request to product details page
  1. Capture parameters submitted from _step 1_ in _step 2_
  1. Choose if to show _step 1_ (options) or _step 2_ (personalization) form
  1. Include params from _step 1_ into _Add to cart_ request at _step 2_

## Functions ##
  * `ZetaPrints_WebToPrint_Helper_2step::isPersonalisationStep()` - Returns _true_ if current stop is _personalisation_
  * ` get_params_from_previous_step ($context)` - Returns list of `<input>` tags for params from _step 1_. All params are taken from a request to a page.

## Affected files ##
### [zp2steptheme/template/catalog/product/view.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zp2steptheme/template/catalog/product/view.phtml) ###
This file shows form for ordering on product page. This form contains product images, product name, product description, product price, etc.

**Section 1**: сheck if current step is not _step 2_ (personalisation) then show standard M. product page, otherwise it jumps into next section.
```
<?php if(!$this->helper('webtoprint/2step')->isPersonalisationStep()): ?>
```

**Section 2**: show web-to-print personalisation form
```
<?php else: ?>
```

**Section 3**: Output image tabs for multipage products with web-to-print feature
```
<?php $this->helper('webtoprint/personalization-form')->get_page_tabs($this); ?>
```

**Section 4**: output list of `<input>` tags for params from step 1 (options)
```
<?php echo $this->helper('webtoprint/personalization-form')->get_params_from_previous_step($this); ?>
```

**Section 5**: output button for showing data sets
```
<?php $this->helper('webtoprint/personalization-form')->getDataSetTable($this); ?>
```

**Section 6**: output input fields, images, stock images, colour pickers and palettes for products with web-to-print feature
```
<?php $this->helper('webtoprint/personalization-form')->get_text_fields($this); ?>
<?php $this->helper('webtoprint/personalization-form')->get_image_fields($this); ?>
<?php echo $this->getChildHtml('webtoprint_palettes'); ?>
```

**Section 7**: output web-to-print buttons for products with web-to-print feature
```
<?php echo $this->getChildHtml('webtoprint_buttons'); ?>
```

**Section 8**: output JavaScript for personalisation form
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

### [zp2steptheme/template/catalog/product/view/addtocart.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zp2steptheme/template/catalog/product/view/addtocart.phtml) ###
This file show _Add to cart_ button, qty input fields and some other information.

**Section 1**: show Add to cart button if current step is personalisation (step 2), otherwise jump to next section
```
<?php if ($this->helper('webtoprint/2step')->isPersonalisationStep()): ?>
```

**Section 2**: show default HTML with Personalise button if current step is personalisation (step 2)
```
<?php else: ?>
```

**Section 3**: change button title to "Personalise"
```
<?php $buttonTitle = $this->helper('webtoprint')->__('Personalise'); ?>
```

**Section 4**: close 'if' opened in Section 1
```
<?php endif; ?>
```

### [zp2steptheme/template/catalog/product/view/media.phtml](http://code.google.com/p/magento-w2p/source/browse/trunk/app/design/frontend/default/zp2steptheme/template/catalog/product/view/media.phtml) ###
This file shows product image, additional images and image zoomer on product page.

**Section 1**: set correct image type and image label
```
$_imageType = $this->helper('webtoprint/2step')->getImageType('image');
$_imageLabel = $this->helper('webtoprint/2step')->getImageLabel($this);
```

**Section 2**: add ID attribute to the element. Replace image type and image label

Replace `'image'` with `$_imageType` and `$this->getImageLabel()` with `$_imageLabel`
```
$_img = '<img id="image" src="'.$this->helper('catalog/image')->init($_product, $_imageType)->resize(265).'" alt="'.$this->escapeHtml($_imageLabel).'" title="'.$this->escapeHtml($_imageLabel).'" />';
```

**Section 3**: replace image type

Replace `'image'` with `$_imageType`
```
echo $_helper->productAttribute($_product, $_img, $_imageType);
```

**Section 4**: remove web-to-print images from the gallery on personalisation form
```
<?php $this->helper('webtoprint/personalization-form')->prepare_gallery_images($this) ?>
```

## Application of 1- or 2-Step process ##
You can have 2 identical themes with the only difference in 1 or 2 step process. Choose the most commonly used theme as the default and enable the other theme for some products only.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)