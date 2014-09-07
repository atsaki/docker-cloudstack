FROM phusion/baseimage:0.9.13

ENV HOME /root
ENV CLOUDSTACK_REPO_URL https://github.com/apache/cloudstack.git
ENV CLOUDSTACK_BRANCH 4.4-forward

# Install required Packages
RUN apt-get update
RUN apt-get install -y build-essential
RUN apt-get install -y libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev git autoconf g++ 
RUN apt-get install -y python2.7-dev python-setuptools python-pip

# Install Java
RUN apt-get install -y python-software-properties
RUN add-apt-repository -y ppa:webupd8team/java
RUN apt-get update
RUN echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN echo debconf shared/accepted-oracle-license-v1-1 seen true | debconf-set-selections
RUN apt-get install -y oracle-java7-installer oracle-java7-set-default maven

# Install MySQL
RUN echo "mysql-server mysql-server/root_password password root" | debconf-set-selections
RUN echo "mysql-server mysql-server/root_password_again password root" | debconf-set-selections
RUN apt-get install -qq -y mysql-server
RUN (/usr/bin/mysqld_safe &); sleep 3; mysqladmin -u root -proot password ''

# Checkout CloudStack
RUN cd $HOME; git clone $CLOUDSTACK_REPO_URL
RUN cd $HOME/cloudstack; git checkout $CLOUDSTACK_BRANCH

# Build CloudStack Simulator
RUN cd $HOME/cloudstack; mvn clean install -P developer -Dsimulator -DskipTests
RUN cd $HOME/cloudstack; \
    (/usr/bin/mysqld_safe &); sleep 3; \
     mvn -Pdeveloper -pl developer -Ddeploydb
RUN cd $HOME/cloudstack; \
    (/usr/bin/mysqld_safe &); sleep 3; \
     mvn -Pdeveloper -pl developer -Ddeploydb-simulator
RUN cd $HOME/cloudstack; \
    (/usr/bin/mysqld_safe &); sleep 3; \
    mysql -e "GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION"

# Add runit scripts
ADD etc/service/mysqld_safe/run /etc/service/mysqld_safe/run
RUN chmod +x /etc/service/mysqld_safe/run

ADD etc/service/cloudstack_simulator/run /etc/service/cloudstack_simulator/run
RUN chmod +x /etc/service/cloudstack_simulator/run

# Regenerate ssh key and remove unnecessary files
RUN /etc/my_init.d/00_regen_ssh_host_keys.sh
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD ["/sbin/my_init"]
