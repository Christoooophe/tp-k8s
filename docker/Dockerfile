FROM eclipse-temurin:17-jammy
ARG FOLDER
WORKDIR /app
COPY .mvn/ .mvn
COPY pom.xml ./

WORKDIR /app/${FOLDER}

COPY mvnw ${FOLDER}/pom.xml ./
RUN ./mvnw dependency:resolve

COPY ${FOLDER}/src ./src
EXPOSE 8080
CMD ["./mvnw", "spring-boot:run"] 