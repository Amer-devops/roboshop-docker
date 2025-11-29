FROM maven:3.9.11-openjdk-17
EXPOSE 8080
WORKDIR /opt/server
COPY pom.xml .
COPY src ./src
RUN mvn clean package
RUN mv target/shipping-1.0.jar shipping.jar
ENV CART_ENDPOINT="cart:8080" \
    DB_HOST="mysql"
CMD ["java","-jar","shipping.jar"]
# CMD ["sleep","1000"]

# # Stage 1: Build
# FROM maven:3.9.11-openjdk-17 AS build
# WORKDIR /opt/server
# COPY pom.xml .
# COPY src ./src
# RUN mvn clean package

# # Stage 2: Run
# FROM openjdk:17-jdk
# WORKDIR /opt/server
# COPY --from=build /opt/server/target/shipping-1.0.jar shipping.jar

# ENV CART_ENDPOINT="cart:8080" \
#     DB_HOST="mysql"

# EXPOSE 8080
# CMD ["java","-jar","shipping.jar"]
