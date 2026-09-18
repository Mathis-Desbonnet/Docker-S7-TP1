# Je créé la base de mon image depuis l'image postgres/alpine
FROM postgres:17.2-alpine AS database_service

#J'ajoute les variables d'environnements nécessaires au fonctionnement de la base de donnée
ENV POSTGRES_DB=db POSTGRES_USER=usr

# Build database : docker build -t mathisdesbonnet/docker_s7-tp1-database .
# Run database : docker run -d --name DockerS7-TP1-Database mathisdesbonnet/docker_s7-tp1-database
# Verify with docker ps -> Correctly show container "Up" 

# Create new network : docker network create-network Docker_S7-TP1-Network 
# 1-1 : We use -e to add environnement variable because the Dockerfile will be on github, and we don't want our password to be available on github !!
# DONT FORGET TO REMOVE YOUR OLD CONTAINER WITH docker rm -f DockerS7-TP1-Database!
# Re-run database : docker run -d -e POSTGRES_PASSWORD=pwd --network Docker_S7-TP1-Network --name DockerS7-TP1-Database mathisdesbonnet/docker_s7-tp1-database 
# Run adminer : docker run -d --network Docker_S7-TP1-Network --name adminer -p 8080:8080 adminer   

# Copy the sql file into our container
COPY /SQL/CreateSchema.sql /docker-entrypoint-initdb.d
COPY /SQL/InsertData.sql /docker-entrypoint-initdb.d

# Rebuild then Re-run and data are shown!

# 1-2 : To have persistent data, i.e., data that stays when we destroy our container
# New run command : docker run -d -v /db-data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=pwd --network Docker_S7-TP1-Network --name DockerS7-TP1-Database mathisdesbonnet/docker_s7-tp1-database 