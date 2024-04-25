FROM ubuntu:18.04

MAINTAINER Anton Lebedev <mailbox@lebster.me>

RUN set -x \
&& { \
echo '#!/bin/bash'; \
echo 'echo "test" >> /tmp/test'; \
} > /root/test.sh \


# Give execution rights on the cron scripts
RUN chmod 0644 /root/test.sh

#Install Cron
RUN apt-get update
RUN apt-get -y install cron

# Add the cron job
RUN crontab -l | { cat; echo "* * * * * bash /root/test.sh"; } | crontab -

# Run the command on container startup
CMD cron
