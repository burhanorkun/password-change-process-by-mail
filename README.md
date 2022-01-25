# Async password change process by mail

To run Apache ZooKeeper on Linux/Unix, we use the following command:
> $ <Absolute Path To Kafka>/bin/zookeeper-server-start.sh ../config/zookeeper.properties

Running Apache Kafka on Linux/Unix To run Apache Kafka on Linux/Unix, we use the following commands:
> $ <Absolute Path To Kafka>/bin/kafka-server-start.sh ../config/server.properties

Since the Email Formatter consumer is supposed to format and send emails, we will be using a dummy Simple Mail Transfer
Protocol (SMTP) server, as it is just for demonstration purposes. For this, fakeSMTP is used, which can be downloaded
from http:/​/​nilhcem.​com/​FakeSMTP/​download.​html. After downloading and unzipping it, the following command can be
used to run fakeSMTP:

> $ java -jar fakeSMTP-<version>.jar

Clicking on the Start Server button will make it start to listen for SMTP requests.

### Running the Email Formatter consumer

After building everything, the following commands can be used to run the Email Formatter consumer:

> $ cd spring-boot-2-email-formatter-consumer
>
> $ mvn spring-boot:run

### Running the User Registration microservice

After building everything, the following commands can be used to run the User Registration microservice:
> $ cd spring-boot-2-user-registration
>
> $ mvn spring-boot:run

After starting the User Registration microservice, an HTTP GET request can be sent to the
http://localhost:8080/users/reset-password/{burhanorkun@gmail.com}
URL with the email as follows:

After some time, the fakeSMTP server window will show the email sent by the Email Formatter

Now, when trying to access the URL
http://localhost:8080/users
, users will be redirected to the login page as follows:
For the username, "burhan" can be used, while for password, the new password in the reset password email can be used.
Then, this will successfully redirect to the URL http://localhost:8080/login and will show the correct response:
