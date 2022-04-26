FROM centos:centos7.9.2009
EXPOSE 8080/tcp
WORKDIR /app
COPY . /app
RUN yum update -y
RUN yum install epel-release wget unzip git -y
RUN wget https://download.java.net/java/GA/jdk16.0.1/7147401fd7354114ac51ef3e1328291f/9/GPL/openjdk-16.0.1_linux-x64_bin.tar.gz
RUN tar -xvf openjdk-16.0.1_linux-x64_bin.tar.gz
ENV JAVA_HOME=/app/jdk-16.0.1
ENV PATH=$PATH:$JAVA_HOME/bin/
RUN wget https://services.gradle.org/distributions/gradle-7.4.2-all.zip
RUN unzip gradle-7.4.2-all.zip
ENV GRADLE_HOME=/app/gradle-7.4.2
ENV PATH=$PATH:$GRADLE_HOME/bin/
RUN wget https://repo.spring.io/artifactory/release/org/springframework/boot/spring-boot-cli/2.6.6/spring-boot-cli-2.6.6-bin.zip
RUN unzip spring-boot-cli-2.6.6-bin.zip
ENV SPRING_HOME=/app/spring-2.6.6
ENV PATH=$PATH:$SPRING_HOME/bin/
RUN git clone https://github.com/pdcong/HelloWorld.git
RUN spring init --build=gradle --dependencies=web --name=hello hello-world
RUN cp HelloWorld/HelloApp.java /app/hello-world/src/main/java/com/example/helloworld/HelloApplication.java
RUN cd /app/hello-world/ && ./gradlew build
CMD cd /app/hello-world/ && ./gradlew bootRun