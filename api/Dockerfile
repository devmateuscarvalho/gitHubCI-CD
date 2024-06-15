FROM eclipse-temurin:21-alpine

ARG DATABASE_URL=none
ARG DATABASE_USER=none
ARG DATABASE_PASSWORD=none
ARG NEW_RELIC_LICENSE_KEY=none
ARG SPRING_PROFILES_ACTIVE=none

ENV TZ=UTC

ENV NEW_RELIC_APP_NAME="API"
ENV NEW_RELIC_LICENSE_KEY=$NEW_RELIC_LICENSE_KEY

ENV SPRING_DATASOURCE_URL=$DATABASE_URL
ENV SPRING_DATASOURCE_USERNAME=$DATABASE_USER
ENV SPRING_DATASOURCE_PASSWORD=$DATABASE_PASSWORD

ENV SPRING_PROFILES_ACTIVE=$SPRING_PROFILES_ACTIVE
ENV SERVER_PORT=80

RUN mkdir -p /usr/src/app/newrelic/logs
RUN chmod 777 /usr/src/app/newrelic/logs

COPY ./api/newrelic/newrelic.jar /usr/src/app/newrelic/
COPY ./api/newrelic/newrelic.yml /usr/src/app/newrelic/
COPY ./api/target/api**.jar /usr/src/app/

WORKDIR /usr/src/app/

EXPOSE 80
CMD ["/bin/sh", "-c", "java -Xmx1536m -javaagent:/usr/src/app/newrelic/newrelic.jar -jar api*.jar"]