# Automatic Backup Utility for Tally-like Systems

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Platform](https://img.shields.io/badge/Platform-Windows-blue)](#)
[![Batch Script](https://img.shields.io/badge/Language-Batch-orange)](#)

An automated backup utility designed specifically for Tally-like accounting systems that lack built-in backup functionality. This batch script creates scheduled backups, compresses them into ZIP archives, and manages old backup files automatically.

## 📋 Table of Contents
- [Features](#-features)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [Usage](#-usage)
- [File Structure](#-file-structure)
- [License](#-license)
- [Support](#-support)

## ✨ Features

- **Automated Backup**: Creates timestamped backups of your Tally data
- **ZIP Compression**: Archives backups to save disk space
- **Cleanup Management**: Automatically deletes old backups to manage disk space
- **Detailed Logging**: Maintains logs of all backup operations
- **Error Handling**: Comprehensive error checking and reporting
- **Configurable**: Easy-to-modify configuration parameters

## 🧰 Prerequisites

- Windows operating system (7/8/10/11)
- PowerShell (pre-installed on Windows 7 and later)
- Administrative privileges (if backing up protected directories)

## 🚀 Installation

1. Download the `release v1.0.txt` file from this repository
2. Rename it to `backup-utility.bat`
3. Place it in a convenient location (e.g., `C:\BackupScripts\`)
4. Modify the configuration section according to your needs

## ⚙️ Configuration

Edit the configuration section at the top of the batch file:

```batch
:: === USER CONFIGURATION SECTION ===
set "source=C:\\path\\to\\your\\source"              :: Source directory to backup
set "target_root=D:\\path\\to\\target"               :: Target folder for ZIP files
set "max_backups=5"                                  :: Max number of ZIP backups to keep
set "log_folder_override="                           :: Optional: custom log folder (leave empty for default)
set "zip_prefix=backup_"                             :: Prefix for ZIP file names
set "log_prefix=backup_process_"                     :: Prefix for log file names
```

### Configuration Parameters Explained

- `source`: Path to your Tally data directory
- `target_root`: Directory where ZIP backups will be stored
- `max_backups`: Maximum number of backup files to keep (older ones will be deleted)
- `log_folder_override`: Optional custom path for log files (empty = use script directory + /logs)
- `zip_prefix`: String added before timestamp in ZIP filenames
- `log_prefix`: String added before timestamp in log filenames

## 💡 Usage

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

### Output
- ZIP archives with timestamped names in the target directory
- Log files in the logs folder showing backup process details
- Automatic cleanup of old backup files

## 📁 File Structure

```
project-root/
├── backup-utility.bat          # Main backup script
├── README.md                   # This documentation
├── LICENSE                     # GPL v3 license
└── docs/                       # Documentation (optional)
    └── configuration-guide.md
```

## 📊 Example Output

After running the script, you'll see:
- `backup_05-12-2023 14-30-25.zip` - Compressed backup with timestamp
- `logs/backup_process_05-12-2023 14-30-25.txt` - Detailed log file

## 🛡️ License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## 🤝 Support

### Issues
If you encounter any problems:
1. Check the log files in the logs directory
2. Verify your configuration settings
3. Ensure you have read/write permissions for source and target directories
4. Create an issue in this repository with:
   - Your configuration settings (with sensitive data removed)
   - Relevant portions of the log file
   - Windows version

### Contributing
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 🙏 Acknowledgments

- PowerShell's `Compress-Archive` cmdlet for ZIP functionality
- Windows batch scripting community for various techniques
- Users who provided feedback for improvements

---

## 📞 Contact

For questions, suggestions, or issues, please open an issue in this repository.
