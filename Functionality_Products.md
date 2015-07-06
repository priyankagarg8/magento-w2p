# Products #
This extension syncs products information between M and ZP.

ZetaPrints products are called templates. They are organized into catalogs. User access is controlled per catalog.

## Product functionality ##
  * download list of catalogs
  * download list of templates per catalog
  * download template details
  * identify new catalogs
  * identify new/updated templates

M is not concerned about catalogs as such. ZP templates can be mixed into different categories within M, but M must carry the catalog ID to grant/deny user access (where needed). The catalog ID is not visible to users.

## List of catalogs ##
This API does not exist in ZP yet. In the making.

This extension should store all information it needs to identify changes in catalogs.

## List of templates per catalog ##
Use http://www.zetaprints.com/help/template-details-api/ document.
Scroll to List of templates (password protected)
This extension should store all information it needs to identify changes in template lists: TemplateID, Created, LastModified.

## Template details ##
Use http://www.zetaprints.com/help/template-details-api/ document.
Scroll to Template details feed (password-protected)
The extension should match ZP template details to M product fields and copy all relevant information into M.
Existing templates are matched by their ID. Catalog ID is secondary. It may change in ZP and has no bearing on how products are presented in M. CatalogID is just another property needed to use ZP API.

## List of fields per template ##
The following fields should be copied into Magento:
  * links to images
  * product name (only when a new product is created)
  * product description (only when a new product is created)
  * template ID
  * created date time
  * modified date time
  * links to large product images
  * links to small product images




