FROM atsaki/cloudstack-simulator:4.5.2

RUN apt-get -y update && \
    apt-get install -qqy \
      python-pip \
      python-dev ; \
    apt-get clean all ; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN pip install --allow-external mysql-connector-python /root/tools/marvin

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]
