# Introduction #

FQ modifies price model to switch to correct price on the fly.
To make this work for configurable products we've overridden Mage\_Catalog\_Model\_Product\_Type\_Configurable\_Price

# Details #

Setting FQ for configurable product is done the same way as for simple products. The only thing to watch for is to set the FQ to super product and not sub-products.

Grouped and Bundle products represent combinations of different products in set QTY's for which you can set prices therefore usage of FQ with them is not needed.