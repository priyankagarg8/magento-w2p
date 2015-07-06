# Introduction #

In-context image editing is disabled by default because of its development state. Store admins can enable it through [custom options](ZetaPrintsCustomConfigurationFile.md) to try it on their M. installations.


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
    <image-edit>
      <in-context enabled="1" />
    </image-edit>
  </webtoprint>
</config>
```

## Adding option to an existing config file ##

You just have to add option to your config file.

  1. Open custom-options.xml file in your editor (you may need to download the file from your M. installation)
  1. If `<image-edit>` tag exist in the file then just add `<in-context enabled="1" />`, otherwise add `<image-edit>` and `<in-context enabled="1" />` tags into `<webtoprint>` one.
  1. Save and upload config file.

After editing the content between `<webtoprint>` and `</webtoprint>` tags in your config file should be similar to:
```
<image-edit>
  <in-context enabled="1" />
</image-edit>
```