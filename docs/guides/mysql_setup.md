# MySQL Setup Guide

## Download and Installation

1. **Download MySQL Installer**
   - Go to [MySQL Downloads](https://dev.mysql.com/downloads/installer/)
   - Download "MySQL Installer for Windows"
   - Choose the larger download (mysql-installer-community-X.X.XX.X.msi)

2. **Run the Installer**
   - Double-click the downloaded MSI file
   - Choose "Developer Default" install type
   - Click "Next" and "Execute" to install prerequisites
   - Wait for installation to complete

3. **Configuration Steps**
   ```
   Step 1: Choose Authentication Method
   - Select "Use Strong Password Encryption"
   
   Step 2: Set Root Password
   - Enter a strong password for root user
   - IMPORTANT: Save this password securely
   
   Step 3: Create Database User
   - User Name: pebs_admin
   - Password: [create a strong password]
   - Host: localhost
   ```

## Database Creation

1. **Open MySQL Command Line Client**
   - Start Menu > MySQL > MySQL Command Line Client
   - Enter root password when prompted

2. **Create Database**
   ```sql
   CREATE DATABASE pebs_management;
   ```

3. **Create User and Grant Privileges**
   ```sql
   CREATE USER 'pebs_admin'@'localhost' IDENTIFIED BY 'your_password';
   GRANT ALL PRIVILEGES ON pebs_management.* TO 'pebs_admin'@'localhost';
   FLUSH PRIVILEGES;
   ```

## Testing Connection

1. **Verify Database Creation**
   ```sql
   SHOW DATABASES;
   ```
   You should see 'pebs_management' in the list

2. **Test User Access**
   ```sql
   EXIT;
   ```
   Then reconnect as pebs_admin:
   ```
   mysql -u pebs_admin -p
   ```
   Enter the password when prompted

## Environment Variables

1. **Add MySQL to System PATH**
   - Right-click Start > System
   - Click "Advanced system settings"
   - Click "Environment Variables"
   - Under System Variables, find "Path"
   - Click "Edit" and "New"
   - Add MySQL bin path (typically C:\Program Files\MySQL\MySQL Server 8.0\bin)
   - Click "OK" on all windows

## Next Steps

After successful installation:
1. Keep your database credentials secure
2. Update the project's .env file with:
   ```
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=pebs_management
   DB_USERNAME=pebs_admin
   DB_PASSWORD=[your_password]
   ```

## Troubleshooting

1. **If MySQL service doesn't start:**
   - Open Services (services.msc)
   - Find "MySQL80"
   - Right-click and select "Start"

2. **If port 3306 is in use:**
   - Open Command Prompt as Administrator
   - Run: `netstat -ano | findstr 3306`
   - Identify and stop the conflicting process

3. **If connection fails:**
   - Verify MySQL service is running
   - Check firewall settings
   - Confirm user credentials
   - Ensure correct port number
