# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a plain PHP package skeleton/template. It's designed to be configured once via `php configure.php` which replaces placeholders throughout the codebase with actual package details.

## Initial Setup

When using this skeleton for the first time, run the configuration script:

```bash
php configure.php
```

This interactive script will:
- Replace all `:vendor_slug`, `:package_slug`, `:author_name`, `VendorName`, `Skeleton`, and other placeholders
- Rename files (e.g., `Skeleton.php` → `YourClassName.php`)
- Optionally remove tools like PhpStan, Pint, or Dependabot
- Delete the configure script itself when done

## Common Commands

### Testing
```bash
composer test              # Run Pest tests
composer test-coverage     # Run tests with coverage
vendor/bin/pest           # Run Pest directly
```

### Code Quality
```bash
composer analyse          # Run PhpStan static analysis (level 5)
composer format           # Format code with Laravel Pint
```

### Development
```bash
composer install          # Install dependencies
```

## Architecture

### Package Structure

- **Testing**: Built on PHPUnit + Pest
  - `TestCase` extends `PHPUnit\Framework\TestCase`
  - Architecture tests in `ArchTest.php` prevent debugging functions (dd, dump, var_dump, print_r)

- **Namespaces**:
  - Main code: `VendorName\Skeleton\`
  - Tests: `VendorName\Skeleton\Tests\`

### Key Configuration Files

- **phpstan.neon.dist**: Level 5 static analysis, checks src directory, uses baseline
- **composer.json**: Supports PHP 8.2+, includes Pest 3.x/4.x and PHPStan
- **pint.json**: Code style configuration (if present)

## Installation

After configuration, users install via:
```bash
composer require vendor/package-name
```

## CI/CD

GitHub Actions workflows:
- **run-tests.yml**: Runs Pest tests on PHP 8.2, 8.3, 8.4 across ubuntu/windows
- **phpstan.yml**: Static analysis
- **fix-php-code-style-issues.yml**: Auto-fixes code style with Pint
- **update-changelog.yml**: Auto-updates CHANGELOG.md
- **dependabot-auto-merge.yml**: Auto-merges Dependabot PRs

## Important Notes

- This is a skeleton repository - all placeholder values should be replaced via `configure.php` before actual development
- The package requires PHP 8.2+
- Uses PSR-4 autoloading
- Plain PHP package with no framework dependencies
