# Usage Examples

This document provides practical examples of how to use the Automatic Backup Utility for Tally-like Systems.

## Quick Start

1. Download the `backup-utility.bat` file
2. Edit the configuration section at the top of the file
3. Run the script manually or schedule it

## Configuration Examples

### Example 1: Basic Tally Backup
```batch
:: === USER CONFIGURATION SECTION ===
set "source=C:\Tally\Data"              :: Your Tally data directory
set "target_root=D:\Backups\Tally"      :: Where to store backup ZIPs
set "max_backups=7"                     :: Keep 7 days of backups
set "log_folder_override="              :: Use default logs folder
set "zip_prefix=tally_daily_backup_"
set "log_prefix=tally_log_"
```

### Example 2: Multiple Data Sources
```batch
:: === USER CONFIGURATION SECTION ===
set "source=C:\MyBusiness\Data"         :: Your business data directory
set "target_root=E:\Backups\Business"   :: Backup destination
set "max_backups=30"                    :: Keep 30 days of backups
set "log_folder_override=F:\Logs"       :: Custom log location
set "zip_prefix=business_backup_"
set "log_prefix=business_log_"
```

## Scheduling with Windows Task Scheduler

### Create a Scheduled Task

1. Open Task Scheduler by typing `taskschd.msc` in Run dialog (Win+R)
2. Click "Create Basic Task..." in the right panel
3. Enter a name like "Tally Daily Backup" and optional description
4. Choose "Daily" as the trigger
5. Set the time to after business hours (e.g., 8:00 PM)
6. Select "Start a program" as the action
7. Browse to select your `backup-utility.bat` file
8. Finish the wizard

### Advanced Scheduling Options

After creating the basic task, you can:
- Modify the task to run whether the user is logged on or not
- Set the task to run with highest privileges if needed for file access
- Configure recovery options if the task fails

## Understanding the Output

When the script runs, it creates:

1. **ZIP Archive** (in the target directory):
   - `backup_05-12-2023 14-30-25.zip` - Compressed backup with timestamp

2. **Log File** (in the logs directory):
   - `backup_process_05-12-2023 14-30-25.txt` - Detailed operation log

3. **Cleanup**:
   - Old backup files beyond `max_backups` limit are automatically deleted

## Sample Log File Analysis

A typical log file will contain entries like:

```
[START] File copy and zip started at 05/12/2023 14:30:25
[INFO] Created new folder: D:\Backups\Tally\05-12-2023 14-30-25
[INFO] Copying files from C:\Tally\Data to D:\Backups\Tally\05-12-2023 14-30-25
[SUCCESS] Files successfully copied.
[INFO] Creating ZIP archive: D:\Backups\Tally\backup_05-12-2023 14-30-25.zip
[SUCCESS] ZIP archive created successfully.
[INFO] Deleted temporary folder: D:\Backups\Tally\05-12-2023 14-30-25
[INFO] Cleaning up old backups... Keeping last 7 backups.
[END] Process ended at 05/12/2023 14:32:10
```

## Troubleshooting

### If backups aren't being created:
1. Check that the source path exists and is accessible
2. Verify that the target path exists and is writable
3. Review the log file for error messages

### If old backups aren't being cleaned up:
1. Confirm that `max_backups` is set to the desired number
2. Check that the script has permission to delete files in the target directory

### If ZIP files aren't created:
1. Verify PowerShell is available (Windows 7+)
2. Check that the Compress-Archive cmdlet is accessible
3. Ensure no other process is accessing the files being backed up