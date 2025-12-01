FROM maven:3.9.11 AS builder
WORKDIR /opt/server
COPY pom.xml .
COPY src ./src
RUN mvn clean package && \
    mv target/shipping-1.0.jar shipping.jar


FROM eclipse-temurin:17-jre-alpine
EXPOSE 8080
# Creates a system group named "roboshop". Creates a system user named "roboshop" and adds it into the "roboshop" group.
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop    
WORKDIR /opt/server
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
COPY --from=builder --chown=roboshop:roboshop /opt/server/shipping.jar .
USER roboshop
# “When container starts, wait 30 seconds, then run the Java application.”
ENTRYPOINT ["sh", "-c", "sleep 30 && java -jar shipping.jar"]





# FROM maven:3.9.11
# EXPOSE 8080
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package
# RUN mv target/shipping-1.0.jar shipping.jar
# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"
# CMD ["java","-jar","shipping.jar"]