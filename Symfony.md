### COMPOSER

1. Update all dependencies of current project

composer update

2. Install dependencies for current project with versions defined in composer.lock

composer install


### CONSOLE

1. List available commands and show the Symfony version

php app/console

2. Display help for given command

php app/console help [command]

3.  Display all configured public services

php app/console container:debug [--show-private] [service_name]

4. Dump all assets to the filesystem

php app/console assetic:dump

5. doctrine:schema:update

Update the database with its new schema. 

Use with --dump-sql and --force


### CACHE

1. Clear the cached information

  php app/console cache:clear 

2. In Server

  php app/console cache:clear --env=prod

  (After clearing cache should set permission to execute following files) 
  
  sudo chmod 777 -R app/logs app/cache

### BUNDLE

Install bundles web assets under a public web directory
php app/console assets:install <target_dir> [--symlink] [--relative]


### Routing

Display current routes for application
php app/console router:debug | grep [router_name]


### Logger

$logger = $this->get('logger');
$logger->debug("your_message");
