# django-sqlserver
Cara install driver django dengan sql server 2014 dan Django 2.11

## Sebelum install pyodbc azure
``` 
sudo apt install dpkg-dev unixodbc unixodbc-dev python-dev libdpkg-perl build-essential libssl-dev libffi-dev
```
## Install pyodbc azure
```
pip install django-pyodbc-azure
```
## Cek Options connection
```
sudo pico /etc/odbcinst.ini
```
hasilnya akan tampil seperti ini
```
[ODBC Driver 17 for SQL Server]
Description=Microsoft ODBC Driver 17 for SQL Server
Driver=/opt/microsoft/msodbcsql17/lib64/libmsodbcsql-17.1.so.0.1
UsageCount=1
```
Copy ODBC Driver 17 for SQL Server -> Masukan pada bagian options di settings.py

## Konfigurasi Database di settings.py
```
DATABASES = {
    'default': {
        'ENGINE': 'sql_server.pyodbc',
        'NAME': 'tesjdjango',               --Nama Database
        'USER': 'sa',                       --User SQL Server
        'PASSWORD': '123456Bb',             --Password SQL Server
        'HOST': '10.10.0.42\\SQLDEVCORE',   --Host
        'PORT': '1433',                     --Port Number

        'OPTIONS': {
                'driver': 'ODBC Driver 17 for SQL Server',
        },
    },
}
```
