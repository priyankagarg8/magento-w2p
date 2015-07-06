# Introduction #

ZetaPrints creates user profiles to manage user data (text and uploaded photos) as well as maintain current session state. It requires synchronisation of user profiles between the Magento site and ZetaPrints.

# User creation #

A user is created in ZP upon a request to update a preview or upload a photo. UserID and password are stored in Magento for future use.

# User session #
At the moment Magento unregistered user is created in ZetaPrints, cookie named "ZP\_ID" is created on client side. Default cookie lifetime is 6 month, witch can be changed in W2puser.php by ZP\_COOKIE\_LIFETIME value. Next time user connects, he is recognized by that cookie regardless Magento session expired or not. See function autoRegister in W2puser.php for additional details.

Please see following Activity diagram for better explanation:

![http://www.zetaprints.com/magento-docs/user.png](http://www.zetaprints.com/magento-docs/user.png)

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)