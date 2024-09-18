# Use the official RHEL UBI 8 minimal base image
FROM registry.access.redhat.com/ubi8/ubi-minimal:8.8

# Install dependencies including Java 17, curl, tar, gzip, and logrotate
RUN microdnf install -y java-17-openjdk-devel curl tar gzip logrotate file && microdnf clean all

# Set environment variables for Java and Tomcat
ENV JAVA_HOME=/usr/lib/jvm/java-17-openjdk
ENV CATALINA_HOME=/usr/local/tomcat

# Download and install Apache Tomcat 10
RUN mkdir -p /usr/local/tomcat && \
    echo "Directory /usr/local/tomcat created" && \
    curl -L -O https://archive.apache.org/dist/tomcat/tomcat-10/v10.1.0/bin/apache-tomcat-10.1.0.tar.gz && \
    echo "Tomcat tarball downloaded" && \
    ls -l apache-tomcat-10.1.0.tar.gz && \
    file apache-tomcat-10.1.0.tar.gz && \
    tar -xzf apache-tomcat-10.1.0.tar.gz -C /usr/local/tomcat --strip-components=1 && \
    echo "Tomcat extracted" && \
    rm apache-tomcat-10.1.0.tar.gz && \
    echo "Tomcat tarball removed"

# Expose Tomcat port
EXPOSE 8080

# Set the default command to run Tomcat
CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]
