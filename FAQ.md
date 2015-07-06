# Introduction #

Check your problem for a possible solution before sending a request for help to support@zetaprints.com.


# No personalization available #
**I installed the extension, imported my templates, but there is no way to personalize the products. I see Add to cart buttons and it adds them directly to the cart if I click on it.**

You are using a custom theme. See CustomThemeNative and CustomTheme2Step pages for customization instructions. Alternatively, use the default ZP theme provided with the plugin. This can be configured on ZP configuration page in Magento.

# Templates won't import #

**Running the profile for templates importing results in "Error in receiving list of catalogs" message.**

  * Double-check the domain name and API key in the configuration.
  * Check that your ZetaPrints profile has no IP address restriction activated.


**Error in receiving detailes for template _template\_guid_. Leaving the template unmodified.**

Check that the template exists in your ZetaPrints portal.

**Error in receiving list of templates for catalog _catalog\_name_**

Check that the catalog exists in your ZetaPrints portal.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)

# Import profiles disappeared after M. upgrade #

You need to re-create ZetaPrints profiles by hand.
In M.'s admin interface, go to System -> Import/Export -> Dataflow - Advanced Profiles and add the following profiles (first line is the name of the profile followed by a code block for the action XML):

ZetaPrints templates synchronization
```
<action type="webtoprint/templates-synchronization" method="parse" />
<action type="webtoprint/products-updating" method="map" />
```

ZetaPrints catalogues creation
```
<action type="webtoprint/catalogues-creation" method="parse" />
```

ZetaPrints virtual products creation
```
<action type="webtoprint/products-creation" method="map" product-type="virtual" />
```

ZetaPrints simple products creation
```
<action type="webtoprint/products-creation" method="map" product-type="simple" />
```