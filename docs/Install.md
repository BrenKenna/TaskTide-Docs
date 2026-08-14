# Installing TaskTide

The repository is packaged with a pre-compiled version of TaskTide, and it is highly recommended to use that instead of installing from source. Gradle wrapper scripts have been provided for both Windows & Linux in the event buliding from source is a requirement, or the repoistory is forked for development work.
<br>
<br>


---

## Pre-built Application

The [release section](https://github.com/BrenKenna/TaskTide/releases/edit/v0.9.0) of this repository contains a zip which contains all TaskTide dependancies, wrapper scripts for running on linux/windows and configuration files which can be adjusted for the [target deployment strategy](Database-Driver-Installation.md).
<br>

``` bash
# 1). Fetch zip
curl -so tasktide.zip https://github.com/BrenKenna/TaskTide/releases/download/v0.9.0/tasktide.zip

# 2). Unpack
unzip tasktide.zip && rm -f tasktide.zip
```
<br>


---

## Docker deployment

To support deployment onto [containerized platforms](https://github.com/BrenKenna/TaskTide/blob/main/tasktide/use-cases/deployment-use-case/tasktide-service/tasktide.Dockerfile). A dockerfile for caching TaskTide in local repository, and docker-compose using [couchDB](https://hub.docker.com/_/couchdb) as the database backend have been provided.
<br>


``` bash
docker image build -t latest -f deployment/Docker/Dockerfile .

```
<br>


---

## Building from Source

The following describes building TaskTide from source using Gradle, different gradle installation scripts have been supplied which download and install gradle if necessary. Linux distributions should [run this script](https://github.com/BrenKenna/TaskTide/blob/main/tasktide/gradlew), and Windows should [run this script](https://github.com/BrenKenna/TaskTide/blob/main/tasktide/gradlew.bat). Development work can fork the repository, download, and open in NetBeans/JetBrains etc IDE. 
<br>