FROM python:3.9
EXPOSE 8080
WORKDIR /opt/server
COPY payment.ini .
COPY *.py .
COPY requirements.txt .
ENV CART_HOST="cart" \
    CART_PORT="8080" \
    USER_HOST="user" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
CMD ["uwsgi", "--ini", "payment.ini"]


# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server
# COPY requirements.txt .
# RUN pip install --no-cache-dir -r requirements.txt
# RUN pip install uwsgi
# COPY payment.ini .
# COPY *.py .
# ENV CART_HOST="cart" \
#     CART_PORT="8080" \
#     USER_HOST="user" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop" \
#     AMQP_PASS="roboshop123"

# CMD ["uwsgi", "--ini", "payment.ini"]
