#Restful web services guide books
https://github.com/in28minutes/spring-microservices-v2/blob/main/02.restful-web-services/01-step-by-step-changes/v2.md#step-35


# microservices
----------------------------------------------------
# microservices guide book :
https://github.com/in28minutes/spring-microservices-v2/blob/main/03.microservices/01-step-by-step-changes/microservices-v2-1.md
	Service which are expose rest
	small well deployed units
	cloud enabled
----------------------------------------------------
Challeges:Fault torrence ,logging all microservices and load maintances for instances,prevent microser down
mutiple configuration for each microservices ,mutiple env, instance for each microservices

Load Balancing => Naming server(Eureka) =>Ribbon(client side load balance)=>Feign(Easier REST clients)

Visibilty and Montinoring =>Zipkin  disturbed Trancing(trace req across mutiple component)=>Netflex API Gateway(Zulu)

Fault Tolereance =>Hystrix (if service down ,config deafult response )
----------------------------------------------------
MicroService =>Dynamic Scaling,Faster cycle release,adpat new technology
----------------------------------------------------
Spring Cloud LoadBalancer instead of Ribbion
Spring Cloud Gateway instead of Zuul
Resilience4ji instead of Hystrix

----------------------------------------------------

Create limit Service

create Config Server =>

in application.properties file 

spring.config.import=optional:config-server:http:localhost:8888

spring.config.import=optional:configserver: instead
spring.cloud.config.import-check.enabled=false
-----------------------------------------------------
connect Spring Cloud Config Server  to  git repoistries with @EnableConfigServer
spring.cloud.config.server.git.uri=file:///c:/opt/git-localconfig-repo

Connect limt-service to Spring Cloud Config Server 
add jar config -client(talk to Spring Cloud Config Server )
spring.application.name=limits-service
spring.config.import=optional:configserver:http://localhost:8888
spring.profiles.active=qa
spring.cloud.config.profile=qa
-----------------------------------------------------
if u want to know the port number from application.properties to spring code using core Enviotement autowire 

if u want make application to run two instance 
open run configuration
apply argument -Dserver.port=8001
-----------------------------------------------------

Communication between two microservices
1)
Currency-convertor-service =>Currency-Exchnage_service =>database

use 
ResponseEnitity rs=RestTemplate().getForEntity("http://localhost:8000/currency-exchange/from/{from}/to/{to}",Currency-convertor,uriVaribale(map));
Currency-convertor cc=rs.getBody();


2)Feign =>spring.cloud.starter-openfeign
1)first create proxy interface of currencyExchangeProxy =>@FeignClient(name="currency-exchnage", url="localhost:8000") =>copy the requesting method defination from controller add  to  proxy interface
@EnableFeignClients in main class
-----------------------------------------------------

now load balancer(Eureka) =>call  Currency-convertor-service =>Currency-Exchnage_service =>database
defining url all time id diffcult
serviceRegistryor/naming server => Register all the microservices


@EnableEurekaServer in main application => application.properties =add name of application and port
to stop register naming micro service has not registering
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
-----------------------------------------------------
Currency-convertor-service <=naming server=>Currency-Exchnage_service =>database

add => eurekanetflexclient in both conversion and exchnage microservices

add eureka url in application properties
-----------------------------------------------------

now lets do commuincate  Currency-convertor-service to mutiple instanceCurrency-Exchnage_service

 in proxy class remove url

  
eureka.instance.prefer-ip-address=true
OR

eureka.instance.hostname=localhost














































Help for Debugging Problems:
Here's the code backup at the end of Step 07: https://github.com/in28minutes/spring-microservices-v2/blob/main/03.microservices/step07.md

Step by Step changes are detailed here:https://github.com/in28minutes/spring-microservices-v2/blob/main/03.microservices/01-step-by-step-changes/microservices-v2-1.md#step-01

Two Recommended Activities:
Activity - 1 : Explore other backups for this section (Steps 08,10,13,15,21,25,29, final) - https://github.com/in28minutes/spring-microservices-v2/tree/main/03.microservices

Activity - 2 : Get Familiar with the structure of Step by Step changes file - https://github.com/in28minutes/spring-microservices-v2/blob/main/03.microservices/01-step-by-step-changes/microservices-v2-1.md#step-01
