# Composer Setup Guide

## Download and Installation

1. **Download Composer Installer**
   - Go to [Composer Download Page](https://getcomposer.org/download/)
   - Click on "Composer-Setup.exe" to download the Windows installer

2. **Run the Installer**
   - Double-click the downloaded Composer-Setup.exe
   - If prompted by Windows security, click "Run"
   - Choose the PHP installation to use (Select the PHP >= 8.1 installation)
   - Allow the installer to set up necessary environment variables

## Verify Installation

1. **Open Command Prompt** or **PowerShell**
2. **Check Composer Version**
   ```bash
   composer --version
   ```
   You should see something like:
   ```
   Composer version 2.5.x ...
   ```

## Create Laravel Project

Once Composer is installed, we can create our Laravel project:

1. **Navigate to Project Directory**
   ```bash
   cd src
   ```

2. **Create New Laravel Project**
   ```bash
   composer create-project laravel/laravel .
   ```

3. **Install Additional Dependencies**
   ```bash
   composer require laravel/breeze --dev
   ```

## Configure Laravel

1. **Copy Environment File**
   ```bash
   copy .env.example .env
   ```

2. **Update Database Configuration**
   Edit `.env` file and update these lines:
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=pebs_management
   DB_USERNAME=pebs_admin
   DB_PASSWORD=your_password
   ```

3. **Generate Application Key**
   ```bash
   php artisan key:generate
   ```

4. **Install Laravel Breeze**
   ```bash
   php artisan breeze:install blade
   
   # Install NPM dependencies
   npm install
   
   # Build assets
   npm run dev
   ```

## Test Installation

1. **Start Laravel Development Server**
   ```bash
   php artisan serve
   ```

2. **Visit Local Site**
   - Open browser
   - Go to http://localhost:8000
   - You should see the Laravel welcome page

## Troubleshooting

1. **If Composer commands fail:**
   - Verify PHP is in your PATH
   - Try running commands as administrator
   - Check PHP version matches requirements

2. **If Laravel installation fails:**
   - Check PHP extensions are enabled
   - Verify Composer is using correct PHP version
   - Ensure all required PHP extensions are installed

3. **Required PHP Extensions:**
   ```bash
   php -m
   ```
   Should include:
   - BCMath
   - Ctype
   - JSON
   - Mbstring
   - OpenSSL
   - PDO
   - PDO_MySQL
   - Tokenizer
   - XML
