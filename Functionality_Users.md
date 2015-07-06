# User management #

Magento store is the primary source of user data. All profiles are stored there. ZP is only concerned about identifying the user for data caching purposes and order assignment.
ZP requires a user ID to be registered before any personalization takes place. If a user is not registered it will be assigned a user ID by ZP and nagged about registration.

## Creating new users ##
A new user is created by making an HTTP POST call with a GUID as a user id (must be unique, like really unique) and a generated password. No other user details are needed.
More here http://www.zetaprints.com/help/user-registration-api/

Magento should store the GUID and password in a user profile or a session so that when the user comes back the same ID and password are used.

## Logging users into ZP automatically ##
When the user is presented with a ZP preview page or flash plugin they should already have user identity information. The call to ZP should contain the user ID and a hash of the user's IP at the moment and the password (http://www.zetaprints.com/help/md5-hash-for-authentication/). This needs to be done only once per session, but it will be more reliable if the info is passed onto ZP every time the user is referred there.
More on the auto-login is here: http://www.zetaprints.com/help/automatic-user-logon/

## Code ##
User management code is placed in _app/code/local/ZetaPrints/Api/Model/W2puser.php_

  * autoRegister() - Registers Magento user in ZetaPrints if he has not already registered.
  * getW2pState() - Returns status of magento user.
  * getW2pUserId() - Returns ZetaPrints' GUID for the registered Magento user.
  * getW2pPass() - Returns ZetaPrints' password for the registered Magento user.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)