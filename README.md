# laravel-docker-compose
setup environment docker: php72-nginx-mysql57

## Require 
+ Turn off all Internet Information Services (IIS) on windows
+ Installed Docker Desktop
+ Search and end task mysql in task manager

## Tutorial
+ clone resource to your directory
+ run cmd in path your directory
+ Install images
```bash
docker-compose up -d
```

+ Restart containers
```bash
docker-compose stop
docker-compose up -d
```

+ Install library project 1
```bash
docker exec -it laravel-php72 bash
cd app1
composer install
exit
```

+ Install library project 2
```bash
docker exec -it laravel-php72 bash
cd app2
composer install
exit
```

+ In hosts file (C:/Windows/System32/drivers/etc) add last row
```bash
127.0.0.1 lhvv.app.test
127.0.0.1 lhvv.app2.test
```
+ Save it (It defined in files default.conf vs app2.conf in path your directory/nginx/sites you can change serve_name at your disposal)
+ Access in browser to links
```bash
http://lhvv.app.test/
https://lhvv.app2.test/
```


## Note:
+ each change file .conf in sites folder after you must restart nginx (docker-compose restart nginx)
