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
```
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
    run(host='0.0.0.0', port=8080)

#create a name for your app.  wsgi reference will look like my-app:app_name
app_name = default_app() 

```


**Create a Service**
```
sudo nano /etc/systemd/system/APPNAME.system
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
WantedBy=multi.user.target
```

sudo systemctl daemon-reload

sudo systemctl start APPNAME

sudo systemctl enable APPNAME

sudo nano /etc/nginx/sites-available/APPNAME

```
server {
    listen 80;
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

sudo ln -s /etc/nginx/sites-available/APPNAME /etc/nginx/sites-enabled/

sudo nginx -t

sudo systemctl restart nginx
