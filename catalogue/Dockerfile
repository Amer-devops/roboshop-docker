FROM node:20.19.5-alpine3.22 as build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install 


FROM node:20.19.5-alpine3.22
# Create a group and user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
EXPOSE 8080
ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
CMD ["server.js"]


# FROM node:20
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# RUN npm install 
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# CMD ["server.js"]