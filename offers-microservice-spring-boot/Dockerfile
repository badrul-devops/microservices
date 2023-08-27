FROM maven as build

WORKDIR /app
COPY . .
RUN mvn install

#jdk
FROM gcr.io/distroless/java11-debian11
WORKDIR /app
COPY --from=build /app/target/offers-0.0.1-SNAPSHOT.jar /app 

EXPOSE 1001

CMD ["java", "-jar", "offers-0.0.1-SNAPSHOT.jar"] 