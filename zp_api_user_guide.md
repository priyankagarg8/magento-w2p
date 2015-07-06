ZetaPrints [web-to-print and image generation system](http://www.zetaprints.com) provides a [simple web-to-print API](http://www.zetaprints.com/help/category/api/) with various functions to create users, control access, generate previews and place orders.
All the functions are called via HTTP GET/POST. We created a set of PHP wrappers to simplify the programming task.

## ZP API Code And Example ##
  1. The source code for PHP wrappers is located under [svn/trunk/zp\_api\_lib](http://code.google.com/p/magento-w2p/source/browse/#svn/trunk/zp_api_lib) .
  1. Example of use zp\_api [here](http://code.google.com/p/magento-w2p/source/browse/trunk/zp_api_lib/zp.test.php) .
  1. Log file after run test or program [here](http://code.google.com/p/magento-w2p/source/browse/trunk/zp_api_lib/zp_api_log.log).

## ZP API Functions Overview ##
  1. Set api key and api url
  1. Catalogs API
    1. Get list of catalogs for the domain from ZP ([Catalogs API](http://www.zetaprints.com/help/catalogs-api/))
    1. Get list of templates of catalog ([Templates API](http://www.zetaprints.com/help/template-details-api/))
  1. Template API
    1. Get details of template ([Templates API](http://www.zetaprints.com/help/template-details-api/))
  1. User API
    1. Regiser new User ([User rego API](http://www.zetaprints.com/help/user-registration-api/))
  1. Order API
    1. Get Order details ([Order Details API](http://www.zetaprints.com/help/orders-api-order-details/))
    1. Saved order completion ([Order files generation API](http://www.zetaprints.com/help/orders-api-generate-output-files/))
    1. Change Order status ([Order status API](http://www.zetaprints.com/help/orders-api-status-change/))

## Include API And Set api key and api url ##
#### Include file ####
The only file needed to utilize the wrappers is api/zp\_api.php
```
include ("api/zp_api.php");
```
#### Set api key and api url ####
This function must be called before any other API wrapper functions to initialize some global variables.

There are 2 main parameters needed for the wrappers to function: [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) and the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal.
```
function zp_api_init($key, $url){}

/**
  * @param	key, comes in form of a GUID, e.g. "1CFFC003-C369-43A2-AFC4-E0AA292F4436"
  * @param	url, a fully qualified domain name including http:// prefix
  * @return	none
  */
```

## Catalogs API ##
ZetaPrints has a 3-level structure: **portal** <sup>1</sup>--><sup>*</sup> **catalog** <sup>1</sup>--><sup>*</sup> **template**. You need to obtain the list of catalogs and then request a list of templates for each of the catalogs. You may want to check access control attribute before requesting a list of template if your site should only show public templates.


#### Get list of catalogs for the domain from ZP ####
```
//1.1. Get list of catalogs for the domain
$list = zp_api_catalog_list();
print_r($list);//process result here
/*
foreach ($list as $cdata){
//process here
}
*/
```

_zp\_api\_catalog\_list()_ function returns
  * Array of catalogs for the domain which is initted at function zp\_api\_init($key, $url)
  * null - if you didn't set [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) or the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal,
  * null - if couldn't find below xml tag in the rss feed.
```
<channel><item></item></channel>
```

#### Get list of templates of catalog ####
You need a Catalog ID as a parameter to call this function. The parameter is a GUID, e.g. "0187C932-6EB2-4DFF-B90E-3B3BB33E9279".
```
//1.2. Get list of templates of catalog
$list_template = zp_api_catalog_detail("_CatalogID_");
print_r($list_template);
/*
foreach ($list_template as $template){
//process here
}
*/
```

_zp\_api\_catalog\_detail("_CatalogID_")_ function returns
  * Array of templates of catalog which has id = _CatalogID_.
  * null - if you didn't set [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) or the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal,
  * null - if couldn't find below xml tag in the rss feed.
```
<channel><item></item></channel>
```

## Get template details ##
Once you have a list of templates from the previous calls you can request template details, one by one. You need a template ID as a parameter. It comes in a form of GUID, e.g. "7AFB079C-BB16-4856-89FF-2E69B5BE303E".

```
//2.1. Get template details
$template = zp_api_template_detail("_TemplateID_");
print_r($template);
/*
//process here
*/
```

_zp\_api\_template\_detail("_TemplateID_")_ function returns
  * Data Detail (data type is array) of Template which has id = _TemplateID_.
  * null - if you didn't set [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) or the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal.

## Register new user ##
One of the requirements to use the preview and order generation functions is having a valid user ID registered in ZetaPrints with access rights to the template. This set of functions works only with public templates.

You must implement user management where a user is identified even before registering, this identification persists between visits, where possible and is synchronized with ZetaPrints User ID at all times.

ZetaPrints caches all user input, including text and uploaded images. If ZetaPrints user id changes then anything the user entered or uploaded before becomes unavailable. Read more in [User registration API](http://www.zetaprints.com/help/user-registration-api/)

```
// Prepare new user id and password
$user = zp_api_common_uuid(); // generate new user ID in ZP format (GUID)
$pass = zp_api_common_pass(); // generate an obscure password
$ret = zp_api_user_register($user, $pass); // Register a new user with ZetaPrints 
echo "regiter=[$ret]";;
```

_zp\_api\_user\_register($user, $pass)_ function returns
  * 0 - existing user, OK
  * 1 - new user registered, OK
  * -1 - failure, try again with different parameters

Registering a new user with _UserID_ and _Password_ matching an existing user is the same as verifying the user exists.

## Order API ##
ZetaPrints Order API allows some manipulation of orders and retrieval of order details.

#### Get Order details ####
This function returns order details as XML. You need to provide a valid ZetaPrints order ID in GUID format. You may already have the Order ID stored in a database or it may be returned as a parameter after personalizing a design in a FRAME or e-cards widget.

```
//Get order details
$id = "_ZetaPrints order ID_";
$order = zp_api_order_detail($id);
print_r($order);
/*
//process here
*/
```

_zp\_api\_order\_detail("_ZetaPrints order ID_")_ function returns
  * Data Detail (data type is array) of ZetaPrints Order which has id = _ZetaPrints order ID_.
  * null - if you didn't set [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) or the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal.

#### Saved order completion ####
When a design is personalized using ZetaPrints in a FRAME or e-cards widget it is saved as a temporary order. No output files are generated at that stage and it is not [billable](http://www.zetaprints.com/help/billing-rules/). The status of such orders is _Saved_.
You can request ZetaPrints to generate output files for _saved_ orders at any time, for example when a payment was received. Note that the saved order will be removed, a new order is created with all the files generated. Such orders are [billable](http://www.zetaprints.com/help/billing-rules/).

```
//Saved order completion
$id = "_ZetaPrints saved order ID_";
$order = zp_api_order_save($id);
print_r($order);
/*
//process here
*/
```

_zp\_api\_order\_save("_ZetaPrints order ID_")_ function returns
  * Data Detail (data type is array) of New ZetaPrints Order.
  * null - if you didn't set [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) or the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal.

#### Change Order status ####
As an order is progressing to shipping and other stages you may need to update the status in ZetaPrints database. It is a good idea to mark past orders as deleted. They won't be [physically deleted](http://www.zetaprints.com/help/order-retention/) straight away.
You need to supply a valid order ID, current status and the new status as parameters. The status will be changed only if the current status you provide matches the status in ZetaPrints database.

```
//Change order status
$id = "_ZetaPrints order ID_";
$order = zp_api_order_change($id, "_new status_", "_current status_");
print_r($order);
/*
//process here
*/
```
_zp\_api\_order\_change("_ZetaPrints order ID_", "_new status_", "_current status_")_ function returns
  * Data Detail (data type is array) of New ZetaPrints Order.
  * null - if you didn't set [ZetaPrints API Key](http://www.zetaprints.com/help/about-web-to-print-api/) or the [domain name](http://www.zetaprints.com/help/category/access-url/) of your ZetaPrints portal.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)