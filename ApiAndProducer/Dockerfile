FROM openjdk:8-jre-alpine

ENV APPLICATION_USER java
RUN adduser -D -g '' $APPLICATION_USER

RUN apk update && apk add bash coreutils
RUN mkdir /app
COPY ApiAndProducer /app/ApiAndProducer/
RUN chown -R $APPLICATION_USER /app
RUN sudo chmod +x /app/wait-for-it.sh
RUN sudo chmod +x /wait-for-it.sh

WORKDIR /app

RUN sudo chmod +x wait-for-it.sh

USER $APPLICATION_USER



CMD ["java", "-server", "-XX:+UnlockExperimentalVMOptions", "-XX:+UseCGroupMemoryLimitForHeap", "-XX:InitialRAMFraction=2", "-XX:MinRAMFraction=2", "-XX:MaxRAMFraction=2", "-XX:+UseG1GC", "-XX:MaxGCPauseMillis=100", "-XX:+UseStringDeduplication", "-jar", "app.jar"]
