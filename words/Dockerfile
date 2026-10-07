FROM maven:3-eclipse-temurin-8 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN --mount=type=cache,target=/root/.m2,sharing=locked mvn -B verify

FROM eclipse-temurin:8-jre-alpine
WORKDIR /app
COPY --from=build /app/target/words.jar ./words.jar
COPY --from=build /app/target/dependency ./dependency
CMD ["java", "-Xmx8m", "-Xms8m", "-jar", "words.jar"]
