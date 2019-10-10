
# spark cluster 

Use dockers to simulate a spark cluster: 1 master, 6 workers, 3 datanode, namenode, etc.



1. Install docker-ce, docker-compose in host OS following: https://docs.docker.com/install/linux/docker-ce/debian/

2. git clone this repo and enter docker_spark

3. start spark cluster by (may del --no-recreate for the first):

   ```
   sudo docker-compose up -d --no-recreate
   ```

4. Download the first three datasets from https://dumps.wikimedia.org/other/pagecounts-raw/2016/2016-08/

5. extract datasets using `gunzip *.gz`, put them in docker_spark/input_files/input/

6. put the whole `input` folder into hdfs:

   ```
   docker exec namenode hdfs dfs -put ./input_files/input /
   ```

7. Download sparkdemo-1.0-SNAPSHOT.jar, put it in jars folder



A `debian:stretch` based [Spark](http://spark.apache.org) container. Use it in a standalone cluster with the accompanying `docker-compose.yml`, or as a base for more complex recipes.



#### enter a running container

```
$ docker ps
CONTAINER ID  IMAGE    COMMAND  CREATED      STATUS      PORTS  NAMES
72ca2488b353  my_image          X hours ago  Up X hours         my_container

$ docker exec -it 72ca2488b353 sh
```





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

