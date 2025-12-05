# Security Policy

## Supported Versions

The following versions of the Automatic Backup Utility are currently supported with security updates:

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | ✅ Yes             |
| < 1.0   | ❌ No              |

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please follow these steps:

1. **Do not** create a public issue in the GitHub repository
2. Contact the project maintainers directly via [INSERT EMAIL ADDRESS]
3. Include the following information in your report:
   - Description of the vulnerability
   - Steps to reproduce the issue
   - Potential impact of the vulnerability
   - Any suggested fixes if known

### What to Expect

After reporting a vulnerability:

1. You will receive an acknowledgment of your report within 48 hours
2. We will investigate the issue and provide an initial response within 7 days
3. If the vulnerability is accepted, we will work on a fix and provide an estimated timeline
4. If the vulnerability is declined, we will explain our reasoning

## Security Best Practices

When using this backup utility, please follow these security practices:

- Run the script with the minimum required privileges
- Ensure your source and target directories have appropriate access controls
- Regularly review and audit your backup logs
- Store backup files in secure locations with proper access controls
- Consider encrypting sensitive backup data

## Dependencies

This script uses PowerShell's built-in `Compress-Archive` cmdlet which is part of Windows. No external dependencies are required that could introduce security vulnerabilities.

## Updates

We recommend keeping your copy of the backup utility updated to the latest version to benefit from security fixes and improvements.