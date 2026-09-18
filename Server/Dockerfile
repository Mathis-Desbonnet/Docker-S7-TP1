FROM eclipse-temurin:21-jdk-alpine AS server-build

# WORKDIR /usr/src
# First part COPY Main.class ./

# Créer ma variable d'environnement pour accèder facilement aux fichiers
ENV MYAPP_HOME=/opt/myapp
#Le set comme dossier de travail
WORKDIR $MYAPP_HOME

# Lancer la commande apk add pour install maven sur alpine
RUN apk add --no-cache maven

# Rajouter mes fichiers dans mon espace de travail
COPY pom.xml .
COPY src ./src

# Créer mon package maven à executer
RUN mvn package -DskipTests

# docker build -t mathisdesbonnet/docker_s7-tp1-server .
# docker run --name Docker_S7-TP1-Server mathisdesbonnet/docker_s7-tp1-server
# Show Hello World !

FROM eclipse-temurin:21-jre-alpine

# Créer ma variable d'environnement pour accèder facilement aux fichiers
ENV MYAPP_HOME=/opt/myapp
# Lancer la commande apk add pour install maven sur alpine
WORKDIR $MYAPP_HOME
# Rajouter mes fichiers dans mon espace de travail depuis mon conteneur jdk
COPY --from=server-build $MYAPP_HOME/target/*.jar $MYAPP_HOME/myapp.jar

# Créer mon executable dans docker
ENTRYPOINT ["java", "-jar", "myapp.jar"]

# docker build -t mathisdesbonnet/docker_s7-tp1-server .
# docker run -p 8080:8080 --name Docker_S7-TP1-Server mathisdesbonnet/docker_s7-tp1-server