FROM atsaki/cloudstack-simulator:4.5.2-marvin

RUN (/usr/bin/supervisord -c /etc/supervisord.conf &); \
    sleep 300 ; \
    python /root/tools/marvin/marvin/deployDataCenter.py -i /root/setup/dev/basic.cfg ; \
    /usr/bin/supervisorctl -c /etc/supervisord.conf stop cloudstack

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisord.conf"]
