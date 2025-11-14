#servir  la imagen del backend con maven
FROM maven:3.9.9-eclipse-temurin-21

#establecer el directorio de trabajo
WORKDIR /app

#copiar todos los archivos del proyecto  en el  directorio  de trabajo
COPY . .

#ejecuta 2 comandos
#1.- Limpiar y copilar  el jar del proyecto
#2.- copiar el jar resultante  al directorio de trabajo con el nombre app.jar

RUN mvn clean package -DskipTests && cp target/*.jar app.jar

#o 8080
EXPOSE 8081

ENTRYPOINT [ "java", "-jar", "app.jar" ]