# Nginx Config for Custom Errors Pages
A small example that shows how we can render our own templates in case of an nginx response error (5xx, 4xx).

## Screenshots

Desktop             |  mobile
:-------------------------:|:-------------------------:
![desktop](https://user-images.githubusercontent.com/90864553/180619593-ec20ea38-7a9a-4d3c-af06-f95079172f3f.PNG)  |   ![mobile](https://user-images.githubusercontent.com/90864553/180619594-ba5ecf3c-3cd4-4fd0-a1cb-08337ce83606.PNG)


## HTTP status code covered:
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 500 Internal Server Error
- 502 Bad Gateway
## Usage
1- Navigate to the default web servers directory:
```
sudo cd /var/www/html/
```
2- Clone this repo:
```
sudo git clone https://github.com/hamza-dev1/ngnix-custom-error-pages
```
3- Navigate to this directory:
```
sudo cd ngnix-custom-error-pages
```
4- Copy nginx config file into nginx configuration directory:
```
sudo cp nginx/errors-config.conf /etc/nginx/
```
5- Move pages folder outside this directory:
```
mv pages ..
```
6- Delete the cloned repo:
```
sudo cd .. && sudo rm -rf ngnix-custom-error-pages/
```
7- Include the configuration inside vhost file `/etc/nginx/site-available/default:`
```
server {
  ...
  include /etc/nginx/errors-config.conf;
  ...
}
```
8- Run nginx check:
```
sudo nginx -t
```
9- If everything works prefectly reload nginx:
```
sudo systemctl reload nginx.service
```
