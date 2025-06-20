
# Updating OpenGRC

Updating OpenGRC can be done manaully or using the new update script (Linux only). The update process described below will update and configure all changes that have been pushed into production for OpenGRC. It will also update all dependencies, regardless of chanes to the codebase, allowing you to keep up with security patches.

### Automated Process (Linux Only)
From the ***installation path***, simply run 
```shell
./update.sh
``` 

For details on exactly what this does, refer to the Manual Pricess below.

### Manual Process
In cases where automated update is not desired or possible, the following can be performed from the ***installation path***. Note that this is the same process the updater script performs

1. Pull the latest code updates
```shell
git pull
```

2. Update all PHP dependencies
```shell
composer update
```

3. Update the database
```shell
php artisan migrate
```

4. Build all the front-end dependencies
```shell
npm run build
```