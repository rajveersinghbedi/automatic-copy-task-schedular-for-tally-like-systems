# Batch Scripting Guide

This guide provides information about the batch scripting techniques used in the Automatic Backup Utility.

## Key Techniques Used

### 1. Delayed Variable Expansion
```batch
setlocal enabledelayedexpansion
```
This allows variables to be expanded at execution time rather than at parse time, which is essential when working with loops and changing variables.

### 2. Date and Time Formatting
```batch
for /f "tokens=2 delims==." %%a in ('wmic os get localdatetime /value') do set datetime=%%a
```
This technique uses WMIC to get the current date and time in a reliable format.

### 3. PowerShell Integration
```batch
powershell.exe -Command "Compress-Archive -Path '%new_folder%' -DestinationPath '%zip_file%' -Force"
```
This demonstrates how batch scripts can leverage PowerShell for advanced functionality like ZIP compression.

### 4. Error Handling
```batch
if %errorlevel% equ 0 (
    echo [SUCCESS] Files successfully copied. >> "%log_file%"
) else (
    echo [ERROR] Error occurred while copying files. >> "%log_file%"
)
```
Proper error checking is crucial for reliable batch operations.

## Best Practices

- Always use `@echo off` to prevent command echoing
- Use `setlocal` to preserve environment variables
- Implement proper error handling with `%errorlevel%` checks
- Use meaningful variable names
- Add comments to explain complex operations
- Use proper file path quoting to handle spaces

## Common Variables

- `%~dp0` - Drive and path of the batch file
- `%date%` and `%time%` - Current date and time
- `%errorlevel%` - Exit code of the last command

## Security Considerations

- Validate all user inputs
- Use quotes around file paths to prevent injection
- Limit the privileges with which the script runs
- Be cautious when using user-provided file paths