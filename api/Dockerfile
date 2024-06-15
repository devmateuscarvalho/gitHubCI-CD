FROM eclipse-temurin:21-alpine

# Definindo argumentos que podem ser passados durante o build
ARG DATABASE_URL=none
ARG DATABASE_USER=none
ARG DATABASE_PASSWORD=none
ARG NEW_RELIC_LICENSE_KEY=none
ARG SPRING_PROFILES_ACTIVE=none

# Configurando variáveis de ambiente padrão
ENV TZ=UTC
ENV NEW_RELIC_APP_NAME="API"
ENV SPRING_DATASOURCE_URL=$DATABASE_URL
ENV SPRING_DATASOURCE_USERNAME=$DATABASE_USER
ENV SPRING_DATASOURCE_PASSWORD=$DATABASE_PASSWORD
ENV SPRING_PROFILES_ACTIVE=$SPRING_PROFILES_ACTIVE
ENV SERVER_PORT=80

# Criando diretório e configurando permissões para logs do New Relic
RUN mkdir -p /usr/src/app/newrelic/logs
RUN chmod 777 /usr/src/app/newrelic/logs

# Copiando arquivos New Relic
COPY ./api/newrelic/newrelic.jar /usr/src/app/newrelic/
COPY ./api/newrelic/newrelic.yml /usr/src/app/newrelic/

# Copiando o JAR da aplicação
COPY ./api/target/*.jar /usr/src/app/

# Definindo o diretório de trabalho
WORKDIR /usr/src/app/

# Expondo a porta
EXPOSE 80

# Comando para rodar a aplicação
CMD ["sh", "-c", "java -Xmx1536m -javaagent:/usr/src/app/newrelic/newrelic.jar -jar /usr/src/app/*.jar"]