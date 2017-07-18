# Setup

## Start site
```
docker-compose up -d
```
Site: http://localhost:8080

## Install some plugins
```
docker-compose run wp plugin install contact-form-7 --activate
docker-compose run wp plugin install wp-smtp --activate
docker-compose run wp plugin install tiny-compress-images --activate
docker-compose run wp plugin install w3-total-cache --activate
# docker-compose run wp plugin install sendgrid-email-delivery-simplified --activate
# docker-compose run wp plugin install https://github.com/wp-premium/advanced-custom-fields-pro/archive/master.zip --activate
# docker-compose run wp plugin install https://github.com/hoaitt/Sitepress-Multilingual-CMS/archive/master.zip --activate
# docker-compose run wp plugin install https://github.com/hoaitt/WPML-String-Translation/archive/master.zip --activate
```


# How to

## How to import export init database

### Export
docker-compose exec db bash -c "mysqldump -uroot -proot wordpress | gzip > /docker-entrypoint-initdb.d/init.sql.gz"

### Import
  - docker mysql will automatically import db at start for first time
  - remove `db` service then restart for re-import if you want start from scratch
  - delete database and import by manual
  - note: `mysqldump -u{user} -p{database} | gzip -f > {database}.sql.gz`
  - note: `gzip -dc < {database}.sql.gz | mysql -u{user} -p{database}`

# How to create a theme by Sage
https://github.com/toancong/wp-sage-doc
