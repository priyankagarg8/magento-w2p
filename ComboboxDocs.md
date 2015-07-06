# Introduction #

Provide Combo Box functionality for certain select elements.


# Details #

Provide Combo Box functionality for certain select elements.
Select elements that will get this functionality must have an `<option>` element
with content '-' (dash).
If such option is detected, it is removed and entire `<select>` element becomes
`combobox`.
To achieve this - jquery autocomplete plugin is used with modifications to allow
adding new content to the list.
With this functionality user can: click on element arrow and select an option
form the menu, click in the input field and start typing and choose option from
autocomplete that pops up, click in input field and enter entirely new text that
will be added to the list of options until user leaves the page.
Regardless which of the above options is used, the value of the input field will
be used for passing data upon form submit.

To enable combo box you need to include in specified order:
```
<script type="text/javascript" src="jquery.js"></script> <!-- Base jQuery library -->
<script type="text/javascript" src="ui/jquery.ui.core.js"></script> <!-- Core part of jquey UI library -->
<script type="text/javascript" src="ui/jquery.ui.widget.js"></script> <!-- Widget part of jquey UI library -->
<script type="text/javascript" src="ui/jquery.ui.button.js"></script> <!-- Button part of jquey UI library -->
<script type="text/javascript" src="ui/jquery.ui.position.js"></script> <!-- Position part of jquey UI library -->
<script type="text/javascript" src="ui/jquery.ui.autocomplete.js"></script> <!-- Autocomplete part of jquey UI library -->
<script type="text/javascript" src="jquery.qtip-1.0.0-rc3.js"></script> <!-- jQuery tooltip plugin -->
<script type="text/javascript" src="js/combobox.js"></script> <!-- Actual combobox plugin -->
```

For production environments it is recommended to minify and compress above files
in to 1 javascript file.

To scan all select elements and determine which should get this feature add
following code in actual html document or an external javascript file that is
loaded after above references:

```
        jQuery(window).load(function(e){
            $('select').each(function(){
                var $self = $(this);
                var isCombo = false;
                var $children = $self.children('option');
                $children.each(function(){
                    var $opt = jQuery(this);
                    if ($.trim($opt.text()) == '-') {
                        isCombo = true;
                        $opt.remove();
                    }
                });
                if (isCombo) {
                    var combo = $self.wrap('<div class="ui-widget"/>').combobox();
                }
            });
        });
```

For styling add:

```
<link type="text/css" href="css/combobox.css" rel="stylesheet"/>
```

Make sure that `href` points to correct path for combobox.css file.