# PHP Setup Guide for Windows

## Download and Installation

1. **Download PHP**
   - Go to [PHP for Windows](https://windows.php.net/download/)
   - Under "VS16 x64 Thread Safe" section, download the ZIP file
   - Current recommended version: PHP 8.1.x or higher

2. **Extract PHP**
   - Create a new folder: `C:\php`
   - Extract the downloaded ZIP contents to `C:\php`

3. **Configure PHP**
   - In the `C:\php` folder, find `php.ini-development`
   - Make a copy and rename it to `php.ini`
   - Open `php.ini` in a text editor
   - Find and uncomment (remove the semicolon) these lines:
     ```ini
     extension=curl
     extension=fileinfo
     extension=mbstring
     extension=openssl
     extension=pdo_mysql
     ```

4. **Add PHP to System PATH**
   - Right-click Start > System
   - Click "Advanced system settings"
   - Click "Environment Variables"
   - Under "System Variables", find "Path"
   - Click "Edit" > "New"
   - Add `C:\php`
   - Click "OK" on all windows

## Verify Installation

1. **Open a new Command Prompt** or **PowerShell**

2. **Check PHP Version**
   ```bash
   php -v
   ```
   You should see something like:
   ```
   PHP 8.1.x (cli)...
   ```

3. **Check Enabled Extensions**
   ```bash
   php -m
   ```
   Verify these extensions are listed:
   - curl
   - fileinfo
   - mbstring
   - openssl
   - pdo_mysql

## Troubleshooting

1. **If PHP command is not recognized:**
   - Verify the PATH was set correctly
   - Try restarting Command Prompt
   - Try restarting your computer

2. **If extensions are missing:**
   - Check php.ini for proper extension configuration
   - Verify extensions are uncommented
   - Make sure DLL files exist in the ext directory

3. **Required Visual C++ Runtime:**
   - If PHP fails to start, you may need Visual C++ Redistributable
   - Download from [Microsoft's website](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist)
   - Install both x64 and x86 versions

## Next Steps

After successful PHP installation:
1. Verify PHP requirements for Laravel:
   ```bash
   php -v
   php -m
   ```

2. Proceed with Composer installation using our Composer setup guide

## Common Issues & Solutions

1. **Missing php.ini:**
   - Copy php.ini-development to php.ini
   - Restart the command prompt

2. **Extension loading fails:**
   - Check extension_dir in php.ini
   - Verify extension files exist
   - Check for Visual C++ Runtime

3. **Path issues:**
   - Double-check System PATH entry
   - Use absolute path: C:\php\php.exe
   - Restart command prompt after PATH changes
