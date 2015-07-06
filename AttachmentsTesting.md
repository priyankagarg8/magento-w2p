# Introduction #

With further developing of file uploader, more and more use cases emerge. This is a list of things to test for attachments extension. When more issues are being solved more test cases should be added here.


# Details #

The things to test for uploader are:
  1. You can upload file with any widget on the page.
  1. You can add more files while once already added are uploading.
  1. You can upload the same file more than once per widget.
  1. In admin table of attachments you should see records for each uploaded file, even if it is the same.
  1. In admin you should be able to download any listed file by clicking on its name. If file is image it might be opened instead of pop up download dialog.
  1. In frontend after file is being uploaded you should be able to click on delete icon. When deleting from frontend, the file is not physically deleted, but detached from order process. So in admin it should still be listed in the table.
  1. When adding product to cart no deleted files should appear as part of the order.
  1. You should be able to complete the order as usual and see order details in customer's account page as usual.
  1. In admin you should be able to click on any file delete link. This should delete the record from file table. If there is more than one file with the same name it should not be affected. Repeating file should still be listed and available for download.
  1. Clicking on order id link(if there is one) should lead to order details page.
  1. Clicking on product link should lead to product editing page.
  1. Selecting one or more file records by their check boxes and clicking submit button in top right of the table should delete selected records.
  1. Clicking 'Delete orphaned' button in top right of the page should delete all files that are not part of an order. I would not recommend doing this in production environment because this will delete also files that are being just uploaded by a customer that is still shopping.
  1. Clicking 'Delete All Old' will delete all files that pass old threshold as set in Attachments settings. By setting appropriate values for orphaned files (like 14 days) you may be sure that no files that are in process of being ordered will be deleted.
  1. "Refresh File Hashes" is a button that will be of use to people having older versions of the extension. Clicking it will refresh duplicate files hashes in database table and will allow safe work of the extension with files that have been previously uploaded.
  1. Test if deleting file that is part of an order affects order display in admin and frontend. In both places, deleted file should not be shown as part of the order. In admin a comment should be shown with names of files that are deleted.
  1. Check if the "Delete all orphaned" action only deletes orphaned files or includes non-orphaned files with identical file names.
If you think of more aspects to test, please add them to above list.