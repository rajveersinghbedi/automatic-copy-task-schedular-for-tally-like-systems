# Quick Start Guide

This guide will help you get started with the Automatic Backup Utility quickly.

## Prerequisites

- Windows operating system (7/8/10/11)
- PowerShell (pre-installed on Windows 7 and later)

## Installation

1. Download `release-v1.0.txt` from the repository
2. Rename it to `backup-utility.bat`
3. Place it in a convenient location (e.g., `C:\BackupScripts\`)

## Configuration

Edit the configuration section at the top of the batch file:

```batch
:: === USER CONFIGURATION SECTION ===
set "source=C:\path\to\your\source"              :: Source directory to backup
set "target_root=D:\path\to\target"               :: Target folder for ZIP files
set "max_backups=5"                                  :: Max number of ZIP backups to keep
set "log_folder_override="                           :: Optional: custom log folder (leave empty for default)
set "zip_prefix=backup_"                             :: Prefix for ZIP file names
set "log_prefix=backup_process_"                     :: Prefix for log file names
```

### Configuration Parameters

- `source`: Path to your Tally data directory
- `target_root`: Directory where ZIP backups will be stored
- `max_backups`: Maximum number of backup files to keep (older ones will be deleted)
- `log_folder_override`: Optional custom path for log files (empty = use script directory + /logs)
- `zip_prefix`: String added before timestamp in ZIP filenames
- `log_prefix`: String added before timestamp in log filenames

## Running the Script

### Manual Execution
1. Double-click the `.bat` file to run it manually
2. Or run from command line: `backup-utility.bat`

### Scheduled Execution
Use Windows Task Scheduler to run the backup automatically:
1. Open Task Scheduler
2. Create Basic Task
3. Set trigger (daily, weekly, etc.)
4. Set action to start a program
5. Point to your `backup-utility.bat` file

## Expected Output

After running the script, you'll see:
- `backup_05-12-2023 14-30-25.zip` - Compressed backup with timestamp
- `logs/backup_process_05-12-2023 14-30-25.txt` - Detailed log file

## Troubleshooting

### Common Issues

1. **Access Denied Errors**: Ensure you have read/write permissions for source and target directories
2. **PowerShell Execution Policy**: If you get execution policy errors, run:
   ```powershell
   Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
   ```
3. **Path with Spaces**: The script handles paths with spaces correctly due to proper quoting

### Log Files

Check the log files in the logs directory for detailed information about backup operations. These are invaluable for troubleshooting issues.