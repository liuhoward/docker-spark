
# spark

A `debian:stretch` based [Spark](http://spark.apache.org) container. Use it in a standalone cluster with the accompanying `docker-compose.yml`, or as a base for more complex recipes.



## docker-compose example

To create a cluster with [docker-compose](http://docs.docker.com/compose):

    docker-compose up -d --no-recreate

The SparkUI will be running at `http://${YOUR_DOCKER_HOST}:8080` with one worker listed. To run `pyspark`, exec into a container:

    docker exec -it docker-spark_master_1 /bin/bash
    bin/pyspark

To run `SparkPi`, exec into a container:

    docker exec -it docker-spark_master_1 /bin/bash
    bin/run-example SparkPi 10

Stop all containers

```
docker-compose stop
```

Remove the application containers:

```
docker-compose rm -f
```

