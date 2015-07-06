# Introduction #

Product creation profiles are used to create M. products for templates which were imported from ZetaPrints account. Products are created with general set of properties. Admin should update other properties using bulk edit to make them operational.


# Details #

Product is created for every template which hasn't been assigned already.

There're two separate profiles for creating "simple" and "virtual" M. products:
  * ZetaPrints simple products creation - use this profile to create "simple" M. products for all un-assigned templates
  * ZetaPrints virtual products creation - use this profile for "virtual" M. products

# Usage examples #

## How to create both "simple" and "virtual" products ##

For example, you have three templates already imported. They names are T1, T2 and T3. You want to use T1 and T2 templates for "simple" products and T3 template for "virtual" one.

  1. Run "ZetaPrints simple products creation" profile to create "simple" products for all imported templates. After it you will have 3 "simple" products in M. store.
  1. Go to "Manage product" page in admin interface and remove "simple" product for T3 template. Now you have two templates (T1 and T2) which are assigned to "simple" products and one un-assigned template (T3).
  1. Run "ZetaPrints virtual products creation" profile to create "virtual" product for all un-assigned templates. In our case there's only one un-assigned template which will be used in profiles. It's T3 template. So, after it you will have two "simple" M. products and one "virtual" product.