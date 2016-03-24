# Large file transfer for the DCC


## Quickstart

### Initialize the database
Initialize the database according to schema.sql:
```
$ python 
>>> from server import database
>>> database.init()
```

### Start up the server
Start up the server in one console:
```
$ python run.py
```

### Generate a Transfer Code
Modify config.py by adding an accepted access code to the `ACCESS_CODES` list
```
`ACCESS_CODES = ['your-access-code']`
```
In the console run the following curl command using your access code to obtain an auth-token valid for 24 hours
```
$ curl -i -X GET -H "X-access-code: your-access-code" http://localhost:5000/get-auth-token
```

### Upload a file:
Create a random gzipped file:
```
$ cat /dev/random | head -c 10000000 | gzip > test.gz
```

Open a browser to `localhost:5000` , then log in using your auth-token.
Add a sample and drop your file to upload the file in chunks of 1MB:


## Setting up the environment

Create and active a new virtual environment:
```
$ virtualenv -p python2.7 .virtualenv
$ source .virtualenv/bin/active
```

Install the dependencies:
```
$ pip install -r requirements.txt
```
