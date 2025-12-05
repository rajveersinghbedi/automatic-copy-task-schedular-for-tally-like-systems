# Configuration Guide

This guide explains how to properly configure the Automatic Backup Utility for your specific needs.

## Main Configuration Parameters

### `source`
The directory that contains your Tally data that needs to be backed up.

**Example:**
```batch
set "source=C:\Tally\Data"
```

**Important Notes:**
- Use forward slashes or double backslashes in paths
- Ensure you have read permissions to this directory
- The script will copy all files in this directory (not subdirectories by default)

### `target_root`
The directory where your ZIP backup files will be stored.

**Example:**
```batch
set "target_root=D:\Backups\Tally"
```

**Important Notes:**
- Ensure you have write permissions to this directory
- Make sure there's enough disk space for your backups
- Backups will be named with timestamps in this directory

### `max_backups`
The maximum number of backup ZIP files to keep. When this limit is reached, older backups will be automatically deleted.

**Example:**
```batch
set "max_backups=10"
```

**Recommendation:**
- For daily backups: 7 (for a week) or 30 (for a month)
- For hourly backups: 24 (for a day)

### `log_folder_override`
Optional parameter to specify a custom directory for log files. If left empty, logs will be stored in a `logs` subdirectory.

**Example:**
```batch
set "log_folder_override=E:\Logs\TallyBackups"
```

### `zip_prefix`
The prefix used for ZIP file names. Timestamp will be appended to this prefix.

**Default:**
```batch
set "zip_prefix=backup_"
```

**Results in files like:**
- `backup_05-12-2023 14-30-25.zip`

### `log_prefix`
The prefix used for log file names. Timestamp will be appended to this prefix.

**Default:**
```batch
set "log_prefix=backup_process_"
```

**Results in files like:**
- `backup_process_05-12-2023 14-30-25.txt`

## Common Configuration Examples

### Example 1: Daily Tally Backups
```batch
set "source=C:\Tally\Data"
set "target_root=D:\Backups\Tally"
set "max_backups=30"                 :: Keep 30 days of backups
set "log_folder_override="           :: Use default logs folder
set "zip_prefix=tally_backup_"
set "log_prefix=tally_log_"
```

### Example 2: Hourly System Backups
```batch
set "source=C:\MySystem\Data"
set "target_root=E:\HourlyBackups"
set "max_backups=24"                 :: Keep 24 hours of backups
set "log_folder_override=F:\Logs"
set "zip_prefix=hourly_"
set "log_prefix=log_"
```

## Setting Up Windows Task Scheduler

To run backups automatically:

1. Open Task Scheduler (taskschd.msc)
2. Click "Create Basic Task"
3. Name: "Tally Backup"
4. Trigger: Daily (or Weekly as preferred)
5. Time: Select appropriate time (e.g., after business hours)
6. Action: "Start a program"
7. Program: Path to your `backup-utility.bat` file
8. Click "OK"

## Troubleshooting Common Issues

### Issue: "Access Denied" Errors
**Solution:** Ensure the user account running the script has read permissions for the source directory and write permissions for the target directory.

### Issue: ZIP files not created
**Solution:** Verify that PowerShell is available (Windows 7 or later) and that the Compress-Archive cmdlet is accessible.

### Issue: Log files not created
**Solution:** Check that the script has write permissions to the logs directory (or specified log folder).

## Security Considerations

- Store backup files in a secure location
- Consider encrypting sensitive backup data
- Regularly test backup restoration procedures
- Keep backup locations separate from source data for disaster recovery