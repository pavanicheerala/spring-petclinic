FROM maven:3.6.3-openjdk-11 as build
RUN git clone https://github.com/pavanicheerala/spring-petclinic.git && \ 
    cd spring-petclinic && \
    mvn package

# jar location /spring-petclinic/target/spring-petclinic-2.7.3.jar

FROM openjdk:11
EXPOSE 8080
COPY --from=build /spring-petclinic/target/spring-petclinic-2.7.3.jar /spring-petclinic-2.7.3.jar
CMD ["java","-jar","/spring-petclinic-2.7.3.jar"]
