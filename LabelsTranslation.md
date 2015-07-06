# Introduction #

M. supports interface translation out of the box. Our web-to-print extension uses it to translate its interface (messages, labels of controls from personalization form and image edit window) to different languages. But titles of pages, title of text and image fields, hints and predefined values from templates were out of the game. Now it's possible to translate them as any other piece of text in M.

# Details #

## Preparing file with translated phrases ##

First of all you have to prepare file with translated phrases to a necessary language. Fill it with original and translated titles of pages, titles of text and image fields, hints and predefined values from templates.

Format of the file is a simple CSV. Also, it should be saved with UTF-8 codepage.

Example:
```
"Phrase to translate","Translation of the phrase"
"Word","Term"
```

The only requirement is a name of the file. It must be called as ZetaPrints\_WebToPrintCustomTranslations.csv

## Uploading the file ##

Upload the file to M. server after you finish translating phrases. The file should be uploaded to app/locale/`<locale_name>` directory of your M. installation, where _locale\_name_ is a name of locale you translated phrases in. For example, locale name for Spanish language is es\_ES, for German language is de\_DE. If locale's directory doesn't exist then simply create it.

## Enabling necessary language (locale) in M. installation ##

You have to enable necessary language (locale) after you create and upload file with translations.

Read how to create separate store per language (locale) at http://www.zetaprints.com/magentohelp/magento-web-to-print-localization/

Or you can switch language (locale) globally in System -> Configuration -> General tab -> Locale Options in admin interface.

**Note.** Be sure to clear Magento cache for the changes to take place.