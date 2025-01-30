
# OpenGRC Installation Guide

This guide walks you through setting up **OpenGRC**, a Laravel 11 application built with Filament 3, from cloning the repository to running the application on your local environment.

## Prerequisites

Before you begin, make sure your system meets the following minimum requirements:

- **PHP**: 8.2 or higher
    - Recommended extensions: `mbstring`, `openssl`, `pdo`, `tokenizer`, `xml`, `ctype`, `json`, `bcmath`, `fileinfo`
- **Composer**: 2.5 or higher
- **Node.js**: 18.0 or higher
- **npm**: 8.0 or higher
- **MySQL or SQLite3**: 5.7 or higher (or MariaDB 10.3 or higher) or SQLite 3
  - **Note**: If you are using MySQL, you will need to create the database FIRST before running the installer. SQLite is perfectly fine for small installations and test environments and requires no additional setup.

You can verify your current versions by running the following commands:

```
php -v
composer --version
node -v
npm -v
mysql --version
```

If any of the requirements are not met, install or update the software accordingly.

---

## Step 1: Clone the OpenGRC Repository

To get started, clone the **OpenGRC** repository from GitHub to your local environment.

```
git clone https://github.com/LeeMangold/OpenGRC.git
```

Navigate into the project directory:

```
cd OpenGRC
```

---

## Step 2: Run the Installer

A new installer is available to help you set up OpenGRC quickly. Run the following command to start the installation process:

```
bash install.sh
```
This will run a number of commands, download the necessary dependencies, and set up the application for you. 

Note: If you need to run this command again, you must delete the database information first by either deleting the databases/opengrc.sqlite file or dropping/recreating your database. If you don't you will encounter errors.

**Alternative** 
If you choose to install like like a traditional Laravel Application, you may do so, but be sure to run "php artisan db:seed" to load default permissions and get important setup steps taken care of.

---

## Step 3: Set Permissions

The file permissions set by the installer are more permissive than necessary, but are in place for ease of installation. You should review the ./set_permissions file, adjust as necessary for your chosen webserver environment, and run it to set the correct permissions for your environment.

---

## Step 4: Log In!
After configuring for your web server, you are now able to log in to your OpenGRC instance using the username and password set during the installation process.


# Setting Permissions

Ensure the necessary directories are writable by the web server:

```
artisan
storage/
bootstrap/cache
storage/*
database/opengrc.sqlite
vendor/bin/*
```

You may also need to adjust group ownership to the web server user, e.g., `www-data` for Nginx or Apache.

---

# Docker Instructions

NOTE: This is out of date and needs to be updated based on new install method.

A Dockerfile is included with OpenGRC that uses SQLite persistence and HTTP on port 80 running on Apache. You can set the following environment variables using the -e <name>=<value> flag in docker run:

```yml
APP_ENV - default: local
APP_DEBUG - default: false, set to true to see detailed error screens.
DB_CONNECTION - default: "sqlite", can be set to "mysql" for a MySQL database.
DB_HOST - default: "localhost"
DB_PORT - default: "", can be set to "3306" for a MySQL database.
DB_DATABASE - default: "/var/www/html/storage/opengrc.sqlite", the database name ("opengrc" for MySQL)
DB_USERNAME - default: "", the database user name.
DB_PASSWORD - default: "", the database password.
```

To run the build, use composer run-script docker-build.
