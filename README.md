# Spring-boot2-Security-SAML2.0-keycloak18
 
 Single Sign-On With SAML 2.0, Spring Boot - Security and Keycloak 18.0.1
 
# Step 1: Start Keycloak
 docker-compose -f docker-compose-keycloak18.yml up

# Step 2: Spring Boot run project:
mvn spring-boot:run

# Step 3: Go to:
http://localhost:8081/

user: **admin**
password: **admin**

# Detailed description and steps for run project found here: 
https://jarmx.blogspot.com/2022/09/single-sign-on-with-saml-20-spring-boot.html
