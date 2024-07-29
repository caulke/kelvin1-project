 # Stage 1: Build the application
FROM openjdk:11 AS BUILD_IMAGE

# Install Maven
RUN apt-get update && apt-get install -y maven git

# Clone the repository and build the project
RUN git clone https://github.com/caulke/kelvin1-project.git
WORKDIR kelvin1-project
RUN git checkout docker && mvn install

# Stage 2: Deploy to Tomcat
FROM tomcat:8-jre11

# Metadata
LABEL "project"="kelvin"
LABEL "Author"="kelvin1"

# Remove default Tomcat webapps
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy the WAR file from the build stage
COPY --from=BUILD_IMAGE /kelvin1-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# Expose port 8080 and run Tomcat
EXPOSE 8080
CMD ["catalina.sh", "run"]
