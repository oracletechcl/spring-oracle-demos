# Spring + Oracle DEMOS

## Requirements

1. Java 11 as a minimum
2. Maven 3.8.4 (or use the included wrapper)
3. An AJD (Autonomous JSON Database). Register for free at https://cloud.oracle.com/free
4. A database wallet

## Demos

### spring-jdbc-demo

Showcases a relational table with a single JSON column.

You must update `spring-jdbc-demo/src/main/resources/application.properties` with the correct settings for your AJD:

```
spring.datasource.url=jdbc:oracle:thin:@<database_name>
spring.datasource.username=<username>
spring.datasource.password=<password>
```

For `<database_name>` enter the TLS authentication details on ADB similar to this: 

```shell
(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1521)(host=jv3bojlg.adb.sa-santiago-1.oraclecloud.com))(connect_data=(service_name=ga4f753fbeae7f7_adbscljson_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))
```
A copy of the wallet should be placed in a directory named `wallet`, adjacent to the `pom.xml` file.

Run the `DemoApplication` class from your IDE or invoke `/.mvnw spring-boot:run` on the command line.

To install `mvnw` run `mvn wrapper:wrapper` in the directory adjacent to the `pom.xml` file



Upon execution, this is what you should see: 

```shell
[opc@demospringboot CODE]$  cd /home/opc/CODE ; /usr/bin/env /usr/lib/jvm/java-11-openjdk-11.0.16.1.1-1.0.1.el9_0.x86_64/bin/java -agentlib:jdwp=transport=dt_socket,server=n,suspend=y,address=localhost:40083 @/tmp/cp_2x5sz0figlubw2peum8msufpk.argfile com.example.demo.DemoApplication 

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.6.1)

2022-09-21 18:52:08.750  INFO 107616 --- [           main] com.example.demo.DemoApplication         : Starting DemoApplication using Java 11.0.16.1 on demospringboot with PID 107616 (/home/opc/CODE/spring-oracle-demos/spring-jdbc-demo/target/classes started by opc in /home/opc/CODE)
2022-09-21 18:52:08.759  INFO 107616 --- [           main] com.example.demo.DemoApplication         : No active profile set, falling back to default profiles: default
2022-09-21 18:52:10.492  INFO 107616 --- [           main] com.example.demo.DemoApplication         : Started DemoApplication in 2.303 seconds (JVM running for 2.908)
2022-09-21 18:52:10.496  INFO 107616 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2022-09-21 18:52:11.789  INFO 107616 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
################
Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
Version 19.16.0.1.0 jdbc:oracle:thin:@(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1521)(host=jv3bojlg.adb.sa-santiago-1.oraclecloud.com))(connect_data=(service_name=ga4f753fbeae7f7_adbscljson_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))
################
Todo[id=1, name='Code', data='{"spring": true}']
Todo[id=2, name='Slides', data='{"status": "WORK_IN_PROGRESS"}']
true
null
2022-09-21 18:52:12.654  INFO 107616 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-09-21 18:52:12.827  INFO 107616 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
```

### spring-soda-demo

Showcases a JSON collection via SODA.
https://docs.oracle.com/en/database/oracle/simple-oracle-document-access/

You must update `spring-soda-demo/src/main/resources/application.properties` with the correct settings for your AJD:

```
spring.datasource.url=jdbc:oracle:thin:@<database_name>
spring.datasource.username=<username>
spring.datasource.password=<password>
```

A copy of the wallet should be placed in a directory named `wallet`, adjacent to the `pom.xml` file.

Run the `DemoApplication` class from your IDE or invoke `/.mvnw spring-boot:run` on the command line.

To install `mvnw` run `mvn wrapper:wrapper` in the directory adjacent to the `pom.xml` file

Upon execution, you should see something like this: 

```shell
$  cd /home/opc/CODE ; /usr/bin/env /usr/lib/jvm/java-11-openjdk-11.0.16.1.1-1.0.1.el9_0.x86_64/bin/java -agentlib:jdwp=transport=dt_socket,server=n,suspend=y,address=localhost:33093 @/tmp/cp_969ynwbbfmb5eepugpafrurca.argfile com.example.demo.DemoApplication 

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::                (v2.6.1)

2022-09-21 18:59:25.758  INFO 108187 --- [           main] com.example.demo.DemoApplication         : Starting DemoApplication using Java 11.0.16.1 on demospringboot with PID 108187 (/home/opc/CODE/spring-oracle-demos/spring-soda-demo/target/classes started by opc in /home/opc/CODE)
2022-09-21 18:59:25.767  INFO 108187 --- [           main] com.example.demo.DemoApplication         : No active profile set, falling back to default profiles: default
2022-09-21 18:59:27.040  INFO 108187 --- [           main] com.example.demo.DemoApplication         : Started DemoApplication in 1.837 seconds (JVM running for 2.431)
2022-09-21 18:59:27.044  INFO 108187 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2022-09-21 18:59:28.300  INFO 108187 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
################
Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
Version 19.16.0.1.0 jdbc:oracle:thin:@(description= (retry_count=20)(retry_delay=3)(address=(protocol=tcps)(port=1521)(host=jv3bojlg.adb.sa-santiago-1.oraclecloud.com))(connect_data=(service_name=ga4f753fbeae7f7_adbscljson_high.adb.oraclecloud.com))(security=(ssl_server_dn_match=yes)))
################
Inserted: {"name":"Code","soda":true}
Inserted: {"name":"Slides","status":"WORK_IN_PROGRESS"}
Key:     9BC778E4C7F7439AB427930AE0AB02AB
Content: {"name":"Code","soda":true}
2022-09-21 18:59:29.462  INFO 108187 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-09-21 18:59:29.593  INFO 108187 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.

```

### spring-mongo-demo

Showcases the Oracle Mongo API via Spring-Data

You must update `spring-mongo-demo/src/main/resources/application.properties` with the correct settings for your AJD:

```
spring.datasource.url=jdbc:oracle:thin:@<database_name>
spring.datasource.username=<username>
spring.datasource.password=<password>
spring.data.mongodb.uri=mongodb://<username>:password>@<database>.<oci_region>.oraclecloudapps.com:27017/<username>?authMechanism=PLAIN&authSource=$external&ssl=true&retryWrites=false&loadBalanced=true
```

A copy of the wallet should be placed in a directory named `wallet`, adjacent to the `pom.xml` file.

Run the `DemoApplication` class from your IDE or invoke `/.mvnw spring-boot:run` on the command line.

To install `mvnw` run `mvn wrapper:wrapper` in the directory adjacent to the `pom.xml` file
