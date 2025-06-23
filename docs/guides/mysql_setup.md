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

## Database Creation Using MySQL Shell

1. **Switch to SQL Mode**
   When you see `MySQL JS >`, type:
   ```
   \sql
   ```
   You should now see `MySQL SQL >`

2. **Connect to MySQL Server**
   ```sql
   \connect root@localhost
   ```
   Enter your root password when prompted

3. **Create Database**
   ```sql
   CREATE DATABASE pebs_management;
   ```

4. **Create User and Grant Privileges**
   ```sql
   CREATE USER 'pebs_admin'@'localhost' IDENTIFIED BY 'your_password';
   GRANT ALL PRIVILEGES ON pebs_management.* TO 'pebs_admin'@'localhost';
   FLUSH PRIVILEGES;
   ```

5. **Verify Database Creation**
   ```sql
   SHOW DATABASES;
   ```
   You should see 'pebs_management' in the list

6. **Test User Access**
   First, exit current session:
   ```sql
   \quit
   ```
   
   Then from command prompt:
   ```bash
   mysqlsh --sql -u pebs_admin -p
   ```
   Enter the password when prompted

## Alternative: Using MySQL Command Line Client

If you prefer using the MySQL Command Line Client instead of MySQL Shell:

1. **Open MySQL Command Line Client**
   - Start Menu > MySQL > MySQL Command Line Client
   - Enter root password when prompted

2. All the same commands will work, but you don't need to switch to SQL mode:
   ```sql
   CREATE DATABASE pebs_management;
   CREATE USER 'pebs_admin'@'localhost' IDENTIFIED BY 'your_password';
   GRANT ALL PRIVILEGES ON pebs_management.* TO 'pebs_admin'@'localhost';
   FLUSH PRIVILEGES;
   SHOW DATABASES;
   ```

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

4. **MySQL Shell Modes:**
   - JS Mode (default): `\js`
   - Python Mode: `\py`
   - SQL Mode: `\sql`
   - Always use SQL mode for database commands
