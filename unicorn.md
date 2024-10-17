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
