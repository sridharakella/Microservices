# Microservices
PCF Microservice to Microservice Communication using service registry


Create a Service registry
1. cf create-service p.service-registry standard service-registry

2. Once service registry is created, cf service <service-name> access the url  to check the service is up and running.

3. Make sure you use the same name (service-registry) in manifest.yml to bind the apps to service registry

          sample manifest:  
                            services:
                            - service-registry
            
4. cd currency-conversion-service 
5. cf push
6. cd currency-exchange service
7. cf push
8. Access the service registry to see apps are binded to service registry 
9. Try accessing the microservice url to test the communication between microservices
http://url-name/currency-exchange/from/USD/to/INR to verify the results



Remote Debugging the apps:

 1. Enable the JBP_CONFIG_DEBUG environment variable, this can be done by editing application manifest.yml or invoking the "cf set-env" command. In this article, we use application manifest as an example.

---
applications:
- name: <APP_NAME>
 memory: 512M
 instances: 1
 path: path/java-app.war
 env:
   JBP_CONFIG_DEBUG: '{enabled: true}'
2. Use "cf push" to deploy the Java application to PCF or Pivotal Web Services.

3. Set up the SSH tunnel for the debug framework via JDWP. 

cf ssh -N -T -L 8000:localhost:8000 <APP_NAME>
Once the SSH tunnel has been created, Eclipse/STS should connect to the localhost:8000 for debug access. Please refer to the detailed instructions in the Java Buildpack Debug Framework.
