FROM ubuntu
RUN echo "Deploying .war file"
CMD date 
ENTRYPOINT [ "echo", "hello" ]

#git docker to clone a git repository 

FROM alpine/git
WORKDIR /app
RUN  git clone https://github.com/isaac-liontech/liontech-online-library-web-app.git

#maven to build 

FROM maven:3.9-amazoncorretto-19 as build 
WORKDIR /app
COPY   --from=repo /app/liontech-online-library-web-app  /app/
RUN mvn test
RUN mvn install
RUN mvn clean package 
