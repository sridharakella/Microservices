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


