# Introduction #

Provide means to have per extension custom configuration without need to change
original extension configuration files.

# Details #

Currently what this change is doing is add support for custom config file.
Name of the file is custom-options.xml and should be added manually to extensions _etc_ folder.
That file is intended to provide a way of storing custom configuration modifications.
Later these configurations can be retrieved using standard Magento configuration API

A sample configuration file content is:

```
<?xml version="1.0"?>
<!-- Sample options file, not to be included in extension distribution -->
<config>
  <webtoprint>
    <cache type="user">
      <enabled>0</enabled>
    </cache>
    <colorpicker>
      <show>0</show>
    </colorpicker>
  </webtoprint>
</config>
```

The only required nodes are _`<config>`_ and _`<webtoprint>`_. Everything between _`<webtoprint>`_ can be retrieved using _getOptions_ method of _ZetaPrints\_WebToPrint\_Model\_Config_ class.
In [app/code/local/ZetaPrints/WebToPrint/Helper/Data.php](http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/local/ZetaPrints/WebToPrint/Helper/Data.php) file there is a method added to handle this. Method name is

```
getCustomOptions($path = null)
```


It accepts optional parameter _$path_ that allows to search for specific config node.
For example from above file, to search for enabled node of cache node you should pass
'cache/enabled' as parameter of the above method. Currently as it was requested the
method is used to retrieve all stored values.
Configuration is returned as SimpleXMLElement object that has all nodes as public members and can be encoded to JSON without modification.

_custom-options.xml_ should not be added as part of the content of the extension, this way there is no chance that it will be overwritten or deleted upon extension update or uninstall.

## XML scheme ##
Users who use special XML editors could use XSD file as a helper while editing custom-options.xml file.

Scheme is available at http://code.google.com/p/magento-w2p/source/browse/trunk/app/code/community/ZetaPrints/WebToPrint/etc/custom-options.xsd

<a href='Hidden comment: 

The way Magento treats configuration files is that every type of configuration file is collected in one configuration object. That means that all config.xml files are merged and any repeating nodes override previous. For this case this means that you can have _custom-options.xml_ file in any extension but to prevent accidental overwriting you should use unique node name after config and put all extension configuration in it.
For example above file could be changed like this:

```
<?xml version="1.0"?>
<!-- Sample options file, not to be included in extension distribution -->
<config>
 <web_to_print>
  <cache type="user">
    <enabled>0</enabled>
  </cache>
  <colorpicker>
    <show>0</show>
  </colorpicker>
 </web_to_print>
</config>
```

To retrieve configuration for web_to_print only you will do
```
Mage::helper("webtoprint")->getCustomOptions("web_to_print");
```

'></a>