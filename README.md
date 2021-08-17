Yet Another Kafka log Handler

This project is currently in BETA and not finished!

## Using the Handler

#### Without authentication

```
import yakh

KAFKA_BROKERS = 'localhost:9092'
KAFKA_TOPIC = 'log_test'
log.addHandler(yakh.KafkaHandler(KAFKA_BROKERS, KAFKA_TOPIC))
```


#### With authentication (PLAIN)

```
import yakh

KAFKA_BROKERS = 'localhost:9092'
KAFKA_TOPIC = 'log_test'
USERNAME = 'batman'
PASSWORD = 'robin_is_lame'
log.addHandler(yakh.KafkaHandler(KAFKA_BROKERS, KAFKA_TOPIC, username=USERNAME, password=PASSWORD))
```

## Building a new pip package

First we will build the next version for pypi test and if that works without problems, then it will be built for pypi production

1. Open setup.cfg and increment the version
2. Build the pypi wheel and source package: 

```
$ python3 -m build
```

3. Upload to pypi test:

```
$ python3 -m twine upload --skip-existing --repository testpypi dist/*
```

4. If the upload to test works, then upload to pypi production

```
$ python3 -m twine upload --skip-existing dist/*
```


## TODO

* If the docker container is shutting down and the buffer has data that cannot be sent to Kafka, write the JSON to a mounted drive that provides persistence.
* import a CA
* certificate authentication
* kerberos authentication
* ability to pass in a configuration dictionary
* multiprocessing.Queue option



