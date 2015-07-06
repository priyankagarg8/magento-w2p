# Troubleshooting #
Common causes of problems with w2p extension for Magento:
  * Incorrect configuration - missing steps, attributes not added, etc.
  * Incorrect settings - check your ZetaPrints portal address.
  * Use of custom theme - use our default theme if you do not know how to integrate the extension into a custom theme.
  * File system permissions - make sure all writable folders have write access for Magento.

## Logging ##

The extension has very detailed logging. Most problems can be resolved by looking at the logs.

Check Logging option ON on ZetaPrints configuration page in Magento. Also enable logging in Magento at _System/Configuration/Developer/Log Settings_ in admin interface. All interactions will be logged into Magento log file (_system.log_) file in the _var/log_ folder of Magento. The file cannot be accessed from outside, unless you explicitly allow so.

## IP restriction ##

Your printer settings may only allow access from a single IP address. The symptom would be an error on data import or no templates are imported when there are definitely new or updated ones.
Go to your ZetaPrints portal, log in as a printer and navigate to API age. Make sure there is no restriction on the IP address or the IP is correct.

## Error on importing ##
  * Check configuration page for correct API key and domain name.
  * Check if the profile XML is copied correctly
  * Read http://www.zetaprints.com/help/import-web-to-print-data/ for more info.

## Nothing imports ##
  * Check if you have any templates to import
  * Check if your settings import hidden templates or just the public ones - there may be nothing to import.
  * Check if you have an IP restriction (see API page on ZP)

## File uploading limit ##

PHP has an option to limit the size of uploaded files. If your customers need to upload files larger than 2MB you have to increase this limit.

Open PHP config file _php.ini_, find _upload\_max\_filesize_ option and set its value in megabytes. For example:

```
; Maximum allowed size for uploaded files.
upload_max_filesize = 10M
```

Also check _post\_max\_size_ option in the PHP configuration file. The value of the option should be bigger than value of _upload\_max\_filesize_ option.

Example:
```
; Maximum size of POST data that PHP will accept.
post_max_size = 12M
```

## XSL support ##
The extension requires XSL (XSLT) support. The presence of an XSL component is checked during the installation. It can be aborted if the component is absent. Contact your sysadmin or the hosting company to have it installed.

[![](http://www.zetaprints.com/help/img/magento_w2p_images/magento_support_text.png)](http://www.zetaprints.com/magento-web-to-print/magento-partners)