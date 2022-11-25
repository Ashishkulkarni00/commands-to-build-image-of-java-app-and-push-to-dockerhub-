# commands-to-build-image-of-java-app-and-push-to-dockerhub-


BUILD APPLICATION.PROPERTIES FILE PRODUCTION READY (by configuring databases with environment variables of credentials)

  Note: first provide local database credentials so that application will get compile and jar file can be built.
  example of application.properties file:
  
  
  spring.datasource.url=jdbc:mysql://${MYSQL_HOST:localhost}:${MYSQL_PORT:3306}/Customer-db1
  spring.datasource.username=${MYSQL_USERNAME:root}
  spring.datasource.password=${MYSQL_PASSWORD:Ashish@8983}
  spring.jpa.show-sql=true
  spring.jpa.properties.hibernate.format_sql=true
  spring.jpa.hibernate.ddl-auto = update
  server.port=8081
  spring.mail.host=smtp.mailtrap.io
  spring.mail.username=${MAIL_USERNAME:82a09e7a84bd3a}
  spring.mail.password=${MAIL_PASSWORD:86eb73cb9dd681}
  spring.mail.properties.mail.transport.protocol=smtp
  spring.mail.port=2525
  spring.mail.properties.mail.smtp.auth=true
  spring.mail.properties.mail.smtp.starttls.enable=true
  spring.mail.properties.mail.smtp.starttls.required=true
  customer.values=FirstName,LastName,Username,Age,Gender,Organization,Industry,Address,Phone Number
  
  
BUILDING A JAR FILE OF THE APPLICATION
  
  go to the location of pom.xml file from terminal
    command: mvn clean install    //this will creat a jar file in target folder.
  run the jar file inside spring boot
    command: java -jar <jar-file-name>.jar
    
    

CREATE A DOCKERFILE FOR THE APPLICATION (name of the file: Dockerfile)
  example of docker file for the java microservice based application:
  
  FROM openjdk                                      //base image
  ADD target/*.jar services.jar                     //copying the jar file into the container 
  EXPOSE 8080                                       //tomcat server port
  ENTRYPOINT ["java","-jar","/services.jar"] 
  
  
  
BUILD DOCKER IMAGE AND PUSH TO DOCKERHUB
  
  build docker image
    command: docker build -t <image name> .
  push to dockerhub
    command: docker push <image name>
  
  
  
  
  
Footer
  
