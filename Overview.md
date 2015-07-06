# About ZetaPrints #
Zetaprints (www.zetaprints.com) is an online personalization engine used for web-to-print and dynamic image generation. The system is based on user-uploaded templates built in vector-graphics applications.
ZetaPrints has a set of APIs (http://www.zetaprints.com/help/category/api/), but it is not extensible on its own as it is a fully hosted system. The API can be used to exchange data with ZetaPrins and consume its services from within other applications.

# About Magento #
Magento is an open source e-commerce platform (www.magentocommerce.com). It has plugins and extensions infrastructure. It's main purpose is to build online stores. The default configuration is limited to public stores. There are extensions to control user access and implement stores with limited user access.

# Selling customized products #

Magento is geared up to selling finished products. A user would normally browse the catalog, add products to cart, pay, download or have them delivered.
Selling template-based products requires one more step - personalization.
Personalization is done by ZetaPrints using ZetaPrints flash plugin (http://code.google.com/p/e-cards-plugin/)

Once the design is customized the control is passed back to Magento along with necessary IDs to complete the order and obtain the files.
The user never leaves the Magento store and is unaware that some services were provided by ZetaPrints.

# Purpose of the project #
The main purpose is to allow e-commerce operators build their online stores using an open source platform and utilize the power of ZetaPrints dynamic image generation and web-to-print back-end.
Different applications need different page layouts, different workflow, different styles. Using Magento as a storefront makes the customization possible. Using ZetaPrints API adds design personalization capabilities.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)