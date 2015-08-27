FROM atsaki/cloudstack-simulator:4.5.2

RUN apt-get -y update && \
    apt-get install -qqy \
      python-pip \
      python-dev ; \
    apt-get clean all ; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip install --upgrade paramiko nose requests ; \
    pip install --allow-external mysql-connector-python mysql-connector-python

RUN wget http://jenkins.buildacloud.org/job/cloudstack-marvin-master/lastSuccessfulBuild/artifact/tools/marvin/dist/Marvin-4.6.0-SNAPSHOT.tar.gz ; \
    tar xvfz Marvin-4.6.0-SNAPSHOT.tar.gz ; \
    pip install ./Marvin-4.6.0-SNAPSHOT ; \
    rm -frv Marvin-4.6.0-SNAPSHOT Marvin-4.6.0-SNAPSHOT.tar.gz

CMD ["/bin/bash"]
