# Wordpress Starter Setup

 ## 1. Prerequisites
  - Docker
  - NodeJS
  - mkcert (`brew install mkcert`)
  - The instructions and commands listed below are for MAC

## 2. Download the code from Github
 Repository URL coming soonn.

## 3. Install the project
Run `yarn install`
This activates some CLI shortcuts for you. No Biggie


## 4. Create a .env file
Rename .env.example to .env and change the values as you see fit.

> Note: The default URL is **www.ocu-wp-starter.localhost**. If you want to update your development url, make sure to update the domain in the .env file (database search and replace will come later.)


## 6. Install SSL Certificate on your local machine
This setup is inspired by the following project: [wordpress-nginx-docker-compose](https://github.com/urre/wordpress-nginx-docker-compose)
```shell
cd cli
./create-cert.sh
```

This script will create a locally-trusted development certificates. It requires no configuration.

> mkcert needs to be installed like described in Requirements. Read more for [Windows](https://github.com/FiloSottile/mkcert#windows) and [Linux](https://github.com/FiloSottile/mkcert#linux)

1b. Make sure your `/etc/hosts` file has a record for used domains. On Max the hosts file can be find at `C:\Windows\System32\drivers\etc`. On Mac it is `/etc/hosts`. Make sure to open it with admin rights.

```
sudo nano /etc/hosts
```

Add your selected domain like this:

```
127.0.0.1 myapp.local
```

## 7. Start Docker on your local machine.
I like to use [Docker Desktop](https://www.docker.com/products/docker-desktop/)

Run `yarn start`

## 8. Search and replace the database for domain name change
If you changed the domain in the step above, you will need to search and replace in the database. Run the following:
yarn search-replace old.url.localhost new.url.localhost

First, log into the docker container for Wordpress
`docker exec -it ocu-wordpress bash`

Then, run the search and replace command like this:
`wp search-replace www.ocu-wp-starter.localhost www.myproject.localhost --allow-root`

## 9. Optional: Change the name of the database
you will need to do this in several places:
 - Re-name the database in phpMyAdmin
 - Update the .env file.
 - More?

## 10. Strart developing!

  - Site URL: [https://www.ocu-wp-starter.localhost](www.ocu-wp-starter.localhost) (or the domain you changed it to)

  - PhpMyAdmin URL: [http://localhost:8082/](http://localhost:8082/)

    - Wordpress Admin: [https://www.ocu-wp-starter.localhost/wp-admin/(https://www.ocu-wp-starter.localhost/wp-admin/)]
  user: ocupop | pswd: testpass

  - See the [readme docs](wordpress/wp-content/themes/starter/README.md) for the starter theme to learn about developing with our custom theme.
