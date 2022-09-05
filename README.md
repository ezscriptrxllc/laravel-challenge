# Laravel Backend Developer Challenge

## Sail
We suggested you to use Sail for this (and any) Laravel application as your default development environment. Anyway, feel free to use any development environment you are comfortable with.

Despite Sail doesn't require prior Docker experience, it's needed to have Docker installed and running. 

### Main commands
* ``./vendor/bin/sail up -d``: Build and run all needed containers (Nginx, PHP FPM, MySQL, Redis, MailHog)
* ``./vendor/bin/sail stop``: Stop all running containers

#### Installing Composer Dependencies For Existing Applications
  If you are developing an application with a team, you may not be the one that initially creates the Laravel application. Therefore, none of the application's Composer dependencies, including Sail, will be installed after you clone the application's repository to your local computer.

You may install the application's dependencies by navigating to the application's directory and executing the following command. This command uses a small Docker container containing PHP and Composer to install the application's dependencies:
```
  docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v $(pwd):/var/www/html \
    -w /var/www/html \
    laravelsail/php81-composer:latest \
    composer install --ignore-platform-reqs
  ```

#### Executing Artisan Commands
Laravel Artisan commands may be executed using the ``artisan`` command:

```
sail artisan queue:work
sail artisan make:model Post
sail artisan make:migration "create test table"
```
