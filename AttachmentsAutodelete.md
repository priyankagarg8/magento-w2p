# Introduction #

Delete uploaded files after set period of time. Automate the task using cron and cronjobs support in Magento.


# Details #

Not all files that are uploaded on product page end up being part of an order. These files are
obsolete and only fill up hard disk. Also after certain period of time, you have completed
your orders and thus files attached to them are of no use besides taking up space.
We are handling these files as 2 cases - files that do not belong to an order (orphaned) and
old files (these are files that have been uploaded some period ago regardless if they are part of an order or not).

Scheduled cron jobs are used to delete both of those file cases. For it to function correctly you have to set periods for either
case in System > Configuration > Attachments Options > Settings.
If any of the periods is 0 or empty ot non integer value, it will be ignored and that type of files will not be deleted.
By default the settings are to delete obsolete files after 30 days and not to delete old files at all.

Bare in mind that Old files include both orphaned files and files used in orders, so if you specify value for old files that is equal or less than the value for orphaned files, the latter is simply ignored since ALL files will be deleted by the former setting anyway.

This is run using Magento cron tab. Unfortunately what crontab entry in magento config files does is to tell Magento which Class::Method to run and how often to create schedules. This means that to have real automation you **HAVE** to set up cron or other automation scheduler on the server.

For reference: http://www.magentocommerce.com/wiki/1_-_installation_and_configuration/how_to_setup_a_cron_job

For cron (most widely used solution):

Recommended setting in production environment is:
```
*/5 * * * * /path/to/php /path/to/magento/cron.php >/dev/null 2>&1
```
The above means that cron on server will run cron.php every 5 minutes. And when it runs it will execute all various crontab jobs found.

For testing and debugging purposes last portion of the cron line could be changed to a log file:
```
*/5 * * * * /path/to/php /path/to/magento/cron.php >>/path/to/magento/var/log/cron.log
```
This way all output from the operation will be logged.

Since setting up cron jobs in some environments is not that simple there is the option of running the same process via admin interface.

To do that follow this procedure:
```
Login in admin;
Go to  Attachments > Manage Attachments;
Click 'Delete All Old' button and click OK in pop up dialog.
```
This will fire off same procedure as auto-deleting option. Same periods are taken into account. If there are files old enough to be deleted, you will get a message with number of files being deleted. If there are no old enough files you will get 'No old enough files found.' message and a link pointing to settings page, where you can adjust periods for file deletion.