# docker-maven-tomcat
Deploy java app 

### Get a maven container
docker run --rm -it maven mvn --version

### Generate a maven project (if you don't have one)
```
docker run --rm -it -v $(pwd):/java-app-src -w /java-app-src maven mvn archetype:generate \
    -DgroupId=com.ddffx.java.example \
    -DartifactId=JavaExample \
    -DarchetypeArtifactId=maven-archetype-webapp \
    -DinteractiveMode=false
```

### Build docker image
```
  docker build -t maven-tomcat .
```

### Run the app container in detached mode
```
docker run -d -p 8080:8080 --name my-maven-tomcat maven-tomcat
```

### Follow logs
```
docker logs -f my-maven-tomcat
```
