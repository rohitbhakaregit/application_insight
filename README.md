# application_insight_demo

In this demo I have created a docker image and used Helm 3 for AKS deployment .

## Steps to follow: 

### Go to dockerbuild directory 

 - 1. Build .jar file [ I have referred https://spring.io/guides/gs/rest-service/]   
 - 2. copy and past your .jar file in dockerbuild directory 

```
  ├── dockerbuild
  │   ├── apm-agent
  │   │   └── applicationinsights-agent-3.0.0-PREVIEW.5.jar
  │   ├── Dockerfile
  │   └── rest-service-0.0.1-SNAPSHOT.jar
```

 - 3. build and push your docker image 

 docker build -t <your hub repo> :<tag>
 docker push <your hub repo>: <tag>

### Now go to helm_installer directory 

- 4. Edit docker image name value in helm3 values.yaml

   e.g:
   ```
   image:
     repository: "1383/application_insight" 
   
   ```
   
   If required edit image tag <appVersion value> in Chart.yaml 


- 5. deploy your application using helm command 

helm install <deployment-name> greeting-api  -n <namespace-name optional>

e.g: 
```
helm install greetings greeting-api/ -n testapi 
```
