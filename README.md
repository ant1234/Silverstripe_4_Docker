# Silverstripe_4_Docker
Dockerized Silverstripe 4 environment based on LAMP

### Requirements:
Composer
PHP 7.3

# Instructions :
### Step 1 . Install SilverStripe 4 ( or choose an existing ss app to dockerize )
composer create-project silverstripe/installer /path/to/project ^4

### Step 2 . Drop the Dockerfile and docker-compose.yml into the root directory of the silverstripe project folder

### Step 3 . Add .env variables
```
# Environment dev or live
SS_ENVIRONMENT_TYPE="dev"
SS_DEFAULT_ADMIN_USERNAME="admin"
SS_DEFAULT_ADMIN_PASSWORD="password"
SS_BASE_URL="http://localhost:9090/"

# DB credentials
SS_DATABASE_CLASS="MySQLPDODatabase"
SS_DATABASE_SERVER="database"
SS_DATABASE_NAME="development"
SS_DATABASE_USERNAME="root"
SS_DATABASE_PASSWORD=""
```

### Step 4 . Build the image and run the containers :
`sudo docker-compose up -d`

### Step 5 . Build the project with :
`docker exec ss_app php ./vendor/silverstripe/framework/cli-script.php dev/build`

### Step 6 . Done! You should see your working app at localhost:9090. Log into the admin with username : admin / password: password

# Useful Commands :

### Shell inside database container
`sudo docker exec -it database /bin/bash`

### Shell inside app container
`sudo docker exec -it ss_app /bin/bash`

### Backup database
`sudo docker exec database /usr/bin/mysqldump -u root development > backup.sql`

### Restore database
`cat backup.sql | docker exec -i database /usr/bin/mysql -u root development`
