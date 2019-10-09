# STAMP DevOps Docker image
This image provides you with a self-contained environment to learn how to use STAMP in your CI/CD.

It contains:
- a fully functional Jenkins instance
- Python 3 installation
- CAMP 0.6.2
- CAMP dependencies:
  - Z3 solver, version 4.7.1
  - Docker
  - Docker Compose

To run it, simply execute:
```
docker run -p 8080:8080 -p 50000:50000 --env -v /var/run/docker.sock:/var/run/docker.sock  danzone/stamp-devops:0.0.1 
```
The `-v /var/run/docker.sock:/var/run/docker.sock` option is needed to share the docker deamons of the host with the CAMP container. CAMP can therefore invoke docker and create “siblings” containers.