# Development Setup Guide

## Prerequisites

Before you begin, ensure you have the following installed on your system:

- PHP >= 8.1
- Composer (Latest version)
- Node.js (LTS version) & NPM
- MySQL 8.0 or MariaDB
- Git

## Initial Setup

### 1. Clone the Repository

```bash
git clone [repository-url]
cd pebs-management-system
```

### 2. Install PHP Dependencies

```bash
composer install
```

### 3. Install Frontend Dependencies

```bash
npm install
```

### 4. Environment Configuration

```bash
# Copy the example environment file
cp .env.example .env

# Generate application key
php artisan key:generate
```

Edit `.env` file with your database credentials:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=pebs_management
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

### 5. Database Setup

```bash
# Run database migrations
php artisan migrate

# Seed the database with initial data (when available)
php artisan db:seed
```

### 6. Storage Setup

```bash
# Create symbolic link for storage
php artisan storage:link
```

## Running the Application

### Development Server

```bash
# Start Laravel development server
php artisan serve

# In a separate terminal, compile and watch frontend assets
npm run dev
```

The application will be available at `http://localhost:8000`

## Development Workflow

### 1. Code Style

This project follows PSR-12 coding standards. We use Laravel Pint for PHP code styling:

```bash
# Check code style
./vendor/bin/pint --test

# Fix code style
./vendor/bin/pint
```

### 2. Testing

```bash
# Run all tests
php artisan test

# Run specific test suite
php artisan test --testsuite=Feature
```

### 3. Frontend Development

```bash
# Compile assets for development
npm run dev

# Compile assets for production
npm run build
```

## Common Issues & Solutions

### 1. Permission Issues

If you encounter storage or cache permission issues:

```bash
# Set proper permissions
chmod -R 775 storage bootstrap/cache
```

### 2. Composer Memory Limit

If Composer runs out of memory:

```bash
COMPOSER_MEMORY_LIMIT=-1 composer install
```

### 3. Database Reset

To completely reset the database during development:

```bash
php artisan migrate:fresh --seed
```

## IDE Setup

### VS Code Extensions

Recommended extensions for this project:

- PHP Intelephense
- Laravel Blade Snippets
- Tailwind CSS IntelliSense
- DotENV
- Git Lens

### PhpStorm Setup

If using PhpStorm:

1. Enable Laravel Plugin
2. Set PHP Interpreter
3. Enable Laravel Idea (optional but recommended)
4. Configure Composer
5. Set up PHP CS Fixer

## Git Workflow

1. Create a new branch for each feature/bugfix
2. Follow conventional commits for commit messages
3. Submit PR for review
4. Ensure all tests pass before merging

## Additional Resources

- [Laravel Documentation](https://laravel.com/docs)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Laravel Breeze Documentation](https://laravel.com/docs/starter-kits#laravel-breeze)
