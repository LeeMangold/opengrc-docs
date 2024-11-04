
# OpenGRC Installation Guide

This guide walks you through setting up **OpenGRC**, a Laravel 11 application built with Filament 3, from cloning the repository to running the application on your local environment.

## Prerequisites

Before you begin, make sure your system meets the following minimum requirements:

- **PHP**: 8.2 or higher
    - Recommended extensions: `mbstring`, `openssl`, `pdo`, `tokenizer`, `xml`, `ctype`, `json`, `bcmath`, `fileinfo`
- **Composer**: 2.5 or higher
- **Node.js**: 18.0 or higher
- **npm**: 8.0 or higher
- **MySQL**: 5.7 or higher (or MariaDB 10.3 or higher)

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

## Step 2: Install Composer Dependencies

Laravel uses Composer for dependency management. Run the following command to install the required PHP packages:

```
composer install
```

Composer will fetch all the necessary packages based on the `composer.json` file and create the `vendor` folder where dependencies will be stored.

If you encounter any issues during the installation, you may need to adjust your PHP settings. For example, ensure your memory limit is sufficient by updating your `php.ini`:

```ini
memory_limit = 512M
```

---

## Step 3: Install Node.js Dependencies

Next, install the JavaScript dependencies required by the project using npm. These include Laravel Mix and any front-end libraries.

```
npm install
```

This will install all the dependencies listed in the `package.json` file, which include tools needed for compiling assets.

---

## Step 4: Set Up Environment Variables

Laravel uses an `.env` file to manage environment-specific settings such as database connections and application keys.

1. Copy the example `.env` file to create your own environment configuration:

   ```
   cp .env.example .env
   ```

2. Open the `.env` file in your preferred editor and update the database connection details. For example:

   ```
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=opengrc
   DB_USERNAME=root
   DB_PASSWORD=your_password
   ```

   Replace `your_password` with the actual password for your MySQL user. You may also need to adjust the `DB_HOST` and `DB_PORT` if you are using a remote or non-default setup.

---

## Step 5: Generate Application Key

Laravel requires an application key for encryption purposes. Run the following command to generate this key:

```
php artisan key:generate
```

This command will set the `APP_KEY` in your `.env` file. It should look something like this:

```dotenv
APP_KEY=base64:somelongrandomstring==
```

Make sure this key is set, as it is crucial for your application's security.

---

## Step 6: Create and Configure the MySQL Database

Now you need to set up the MySQL database that Laravel will use. If you haven’t already created one, follow these steps:

1. Log in to your MySQL server:

   ```
   mysql -u root -p
   ```

   Replace `root` with your database username if it’s different. After running this command, you will be prompted to enter your MySQL password.

2. Create a new database for OpenGRC:

   ```
   CREATE DATABASE opengrc;
   ```

3. Exit the MySQL shell:

   ```
   exit;
   ```

Once the database is created, your `.env` file should already be configured to connect to this database.

---

## Step 7: Run Database Migrations and Seeders

With the database set up, you can now create the necessary tables and seed them with initial data.

1. Run the database migrations to create tables:

   ```
   php artisan migrate
   ```

2. After the migrations are complete, run the seeder to populate the database with initial data:

   ```
   php artisan db:seed
   ```

This will set up your database with the necessary schema and initial data required for the application to function.

---

## Step 8: Compile Front-End Assets

Next, compile the front-end assets using Laravel Mix. This step will bundle JavaScript and CSS files for your application.

1. Compile for development:

   ```
   npm run dev
   ```

2. Alternatively, for production builds, you can run:

   ```
   npm run build
   ```

This will minify your assets and optimize them for production environments.

---

## Step 9: Start the Development Server

To start the application locally, you can use Laravel’s built-in development server:

```
php artisan serve
```

This will serve the application at [http://localhost:8000](http://localhost:8000). Open your browser and navigate to this URL to access the application. This is NOT recommended for production. Please use a production web server like Nginx or Apache.

---

## Additional Steps

### Setting Up a Production Environment

If you are deploying OpenGRC in a production environment, ensure you:

- Set the correct file permissions (especially for storage and bootstrap/cache).
- Adjust the `.env` file to reflect your production settings, such as turning off debug mode.
- Configure a web server like **Nginx** or **Apache** to serve the `public` directory as the root.
- Use a process manager like **Supervisor** to keep your Laravel application running.

### Setting Permissions

Ensure the necessary directories are writable by the web server:

```
chmod -R 775 storage
chmod -R 775 bootstrap/cache
```

You may also need to adjust group ownership to the web server user, e.g., `www-data` for Nginx or Apache.

---

## Credentials
PLEASE CHANGE THE DEFAULT ADMIN PASSWORD AFTER INSTALLATION!
```yml
User: admin@example.com
Pass: password
```

---

## Docker Instructions

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
