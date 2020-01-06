# Silverstripe_4_Docker
Dockerize your Silverstripe 4 environment ( based on LAMP )

### Requirements:
Composer
PHP 7.3

# Instructions :
### Step 1 . Install SilverStripe 4 ( or choose an existing ss app to dockerize )
`composer create-project silverstripe/installer /path/to/project ^4`

### Step 2 . Drop the files from this repo ( minus the readme ) into the root directory of your Silverstripe 4 project folder.

### Step 3 . Rename .env.example to .env ( and add to your .gitignore file ), this will set the Silverstripe environment variables that docker will use.

### Step 4 . Build the image and run the containers :
`sudo docker-compose up -d`

### Step 5 . Build the project with :
`sudo docker exec ss_app php ./vendor/silverstripe/framework/cli-script.php dev/build`

### Step 6 . Done!
You should see your working app at `localhost:9090`
Log into the admin at `localhost:9090/admin`
username : `admin`
password : `password`

# Useful Commands :

### Shell inside database container
`sudo docker exec -it database /bin/bash`

### Shell inside app container
`sudo docker exec -it ss_app /bin/bash`

### Backup database
`sudo docker exec database /usr/bin/mysqldump -u root development > backup.sql`

### Restore database
`cat backup.sql | docker exec -i database /usr/bin/mysql -u root development`
