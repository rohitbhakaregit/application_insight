FROM openjdk:8-jre-slim
ARG WORKDIR="/app"
RUN mkdir ${WORKDIR}
ENV JAVA_OPTIONS=""
ENV APPLICATIONINSIGHTS_CONNECTION_STRING=""
ADD apm-agent/ ${WORKDIR}/
ADD *.jar ${WORKDIR}/app.jar
WORKDIR ${WORKDIR}
EXPOSE 8080
RUN printf "#!/bin/sh\nexec java \${JAVA_OPTIONS} -jar app.jar   \${@}\n" > entrypoint.sh && chmod 755 entrypoint.sh
ENTRYPOINT [ "/app/entrypoint.sh" ]                          
