### PHP Laravel CRUD App for DevOps Testing

## Run the Application
```bash
npm install
```
```bash
composer update
```
```bash
php artisan migrate
```
```bash
php artisan serve
```
If we need
```bash
php artisan db:seed
```

Install Apache, MySQL & PHP
```bash
apt-get update
apt-get upgrade
apt-get install apache2 -y
apt-get install mysql-server -y
sudo mysql_secure_installation # for assign security
```
Console ask we some questions.
- Would you like to setup VALIDATE PASSWORD component? Press y|Y for Yes, any other key for No: y
- Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 2
- Remove anonymous users? (Press y|Y for Yes, any other key for No) : y
- Disallow root login remotely? (Press y|Y for Yes, any other key for No) : n
- Remove test database and access to it? (Press y|Y for Yes, any other key for No) : y
- Reload privilege tables now? (Press y|Y for Yes, any other key for No) : y

Login to MySQL
```bash
sudo mysql
sudo mysql -u root -p
```

Authentication credential setup
```bash
SELECT user, host FROM mysql.user;
SHOW DATABASES;
CREATE USER 'root'@'localhost' IDENTIFIED BY 'Sql@054003'; # if exist then
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Sql@054003';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION; # or
GRANT ALL PRIVILEGES ON YourDatabase.* TO 'root'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

IP & Port binding for remote access using Azure Data Studio/MySQL Workbench (Optional)
```bash
netstat -tulpen #Check mysql server is listening on a socket with netstat:
bind-address = 0.0.0.0 # we may bind IP & port each other in `/etc/mysql/my.cnf` file
```

PHP install
```bash
apt-get install php -y
apt-get update
php -v
# some require extension install
sudo apt install php-fpm php-json php-pdo php-mysql php-zip php-pdo php-mbstring php-curl php-xml php-pear php-bcmath
php -m # check installed extension.
```
[Check the server requirement of laravel](https://laravel.com/docs/10.x/deployment#server-requirements)

Composer install
```bash
apt-get install composer -y
composer # check whether
```

Clone & give permission the application into html directory
```bash
git clone https://github.com/jakir-ruet/php-laravel-crud-app.git
chmod -R 775 html
chmod -R 775 php-laravel-crud-app
nano /etc/hosts
172.16.246.132 phplaravel.app
```

In .env file
```bash
APP_NAME=Laravel
APP_ENV=production
APP_KEY=base64:/zvzlgYJYDCUE1dzUaRDc5MZS6jugi1Tc1II2KQ0Gts=
APP_DEBUG=false
APP_URL=http://phplaravel.app
```
```bash
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=dbcrud
DB_USERNAME=root
DB_PASSWORD=Sql@054003
```
```bash
composer update
php artisan key:gen
```