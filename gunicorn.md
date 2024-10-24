# Gunicorn

In Bottle for Run()
```
if __name__ == "__main__":
    run(host='0.0.0.0', port=8080)
```

```
gunicorn --workers 4 app:myapp
```

```
ps aux | grep gunicorn
```

```
sudo kill -9 <PID>
```


```
gunicorn --workers 4 --bind 0.0.0.0:8080 gtest:app
```

## Basic Setup

**Prerequisite:**

You may want to create a specific user account for this app to run under.  Such as a user account named **www**
```
sudo adduser www
```

```
sudo apt install nginx
mkdir appname
cd appname
sudo apt install python3-venv
python3 -m venv VENVNAME
source VENVNAME/bin/activate
python3 -m pip install bottle
python3 -m pip install gunicorn
```
**my-app.py**

When everything is setup you will have to restart your app service (not NGINX) for changes to show to users
```
from bottle import route, run, default_app

@route('/')
def index():
    return('hello world')

if __name__ == "__main__":
    run(host='0.0.0.0', port='8080')

#create a name for your app.  wsgi reference will look like my-app:app_name
app_name = default_app() 

```


**Create a Service**
```
sudo nano /etc/systemd/system/APPNAME.service
```
```
[Unit]
Description=My Cool App
After=network.target

[Service]
User=USERNAME
Group=www-data
WorkingDirectory=/home/USERNAME/APPFOLDER
Enviornment="PATH=/home/USERNAME/APPNAME/VENVNAME/bin"
ExecStart=/home/USERNAME/APPNAME/VENVNAME/bin/gunicorn --workers 3 --bind 127.0.0.1:8000 SCRIPTNAME:APPNAME

[Install]
WantedBy=multi-user.target
```

sudo systemctl daemon-reload

sudo systemctl start APPNAME

sudo systemctl enable APPNAME

    - Go go 127.0.0.1:8000 in web browser and app should be displayed

sudo nano /etc/nginx/sites-available/default

Delete everything in file

```
server {
    listen 80 default_server;
    server_name 127.0.0.1;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

sudo nginx -t

sudo systemctl restart nginx

# SOCKET

sudo chown -R /home/www www:www-data

```
[Unit]
Description=My cool app
After=network.target

[Service]
User=www
Group=www-data
WorkingDirectory=/home/www/myapp
Environment="PATH=/home/www/myapp/venv/bin"
ExecStart=/home/www/myapp/venv/bin/gunicorn --workers 3 --bind unix:myapp.sock  myapp:myapp
[Install]
WantedBy=multi-user.target
```

sudo nano /etc/nginx/sites-available/default
```
server {
        listen 80 default_server;
        server_name 127.0.0.1;

        location / {
                proxy_pass http://unix:/home/www/myapp/myapp.sock;
                proxy_set_header Host $host;
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-Proto $scheme;
        }
}
```
