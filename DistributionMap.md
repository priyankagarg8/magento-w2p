# Introduction #

Distribution map allows the user to mark an area using series of clicks on the map.
It is based on Google maps JavaScript API v3. v3 is the latest API for google maps and is highly optimized for speed and compatibility with portable devices (mobiles, tablets etc.)



# Details #

Distribution map (DM) is implemented in Magento as a JavaScript custom option.
That means that most of its frontend functionality is done using JavaScript to replace some content on the web page with a map.
Reason for this is that custom options in Magento are not very extendable, put simply they are hard coded and adding new options would mean overwriting core classes and template files. This approach is prone to problems with future updates of core files, and also the possibility to have another extension, which will need to override same files, installed alongside.
The way DM is done does not override any core files. It depends on magento sales system to provide needed data
To make a DM custom option you have to login to backend as admin. Go to product of choice. Add custom option to the product. The custom option should be of type **field** and have a title ending on **`*``*``*`kml`*``*``*`**.

Example: _Distribution map `*``*``*`kml`*``*``*`_

Rest of the settings are as usual - price correction, sku, order etc.

It is crucial to have title in above format, this is what DM code uses to detect a map option both in frontend and backend code.

When product page is opened with a custom option following above rules, DM JavaScript starts and puts a map on top of the default text field and the field is hidden using css rule 'visibility: hidden'

When map is shown initially it is partially covered with an explanation text about what user should do with it. In the text there is a _Start now_ link that closes the hint overlay and allows map to take interactions.

The user outlines desired area by clicking on the map. Each click point is connected with previous with 3px wide red line. Last point is auto connected to first point, and space in between the lines is filled with semi transparent red color.

On last clicked point there is a marker displayed. Clicking on the marker will delete last point and put marker on next last point. You can click on the marker until the first point is deleted.

Clicking on the shape it self raises JavaScript confirmation alert asking whether to delete entire shape and start over.

Initially map is centered above location set in admin settings at a zoom level that can also be set there.
In top part of the map there is a search text box where user can enter an address and click Search button next to it. Then Google services will do their best to find a match.
When match is found, the map is centered on top of it and an Info window is shown with the address that Google shows and its coordinates.

After every click, the coordinates are saved as value of the original text field. This way we are actually providing value for it and it will be saved easily by Magento built in system without much effort from us. This is especially helpful when the option is required and its presence is verified upon adding product to cart.

The idea behind this map is to be able to outline an area and then get it as a KML file. So to achieve that, we have registered an observer class that processes each submitted product option and if it finds that it represents a map, the KML content is generated and saved in a table, alongside with actual coordinates, quote id, option id and order id. Generated KML is presented for download after order is completed. It is available in order details page both in frontend and admin as a link that will prompt user/admin to download kml file.

After a product with map is added to cart, there is a preview of the outlined area in cart page and in checkout page (last step). The preview is also a Google map but it does not react to clicks so no changes to the polygon can be made.

The maps on different pages have different sizes. This sizes can be set in Admin > System > Configuration > Google API > Google Maps Settings.
There are 3 sizes:

  1. Product page
  1. Cart page (that size is used for checkout and frontend order details pages too)
  1. Admin page

There you will find also a setting whether used device has GPS capabilities. Setting this to 'YES' on device that has no such capabilities won't do any harm.