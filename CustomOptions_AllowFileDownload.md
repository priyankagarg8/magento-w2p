# Introduction #

This options allows users download files regardless of ZP template setting.

**Note:** the option is applied for existing and future orders.

# Details #

## Using custom options for the first time ##

If you're using custom options for the first time, you have to create a config file.

  1. Open your preferred text editor
  1. Put following content into it
  1. Save as custom-options.xml
  1. Upload the file to app/code/local/ZetaPrints/WebToPrint/etc directory on your M. installation.

Content of custom-options.xml file:
```
<config>
  <webtoprint>
    <file-download>
      <users allow="1" />
    </file-download>
  </webtoprint>
</config>
```

## Adding option to an existing config file ##

You just have to add option to your config file.

  1. Open custom-options.xml file in your editor (you may need to download the file from your M. installation)
  1. If `<file-download>` tag exist in the file then just add `<users allow="1" />`, otherwise add `<file-download>` and `<users allow="1" />` tags into `<webtoprint>` one.
  1. Save and upload config file.

After editing the content between `<webtoprint>` and `</webtoprint>` tags in your config file should be similar to:
```
<file-download>
  <users allow="1" />
</file-download>
```