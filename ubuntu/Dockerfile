FROM ubuntu:22.04

MAINTAINER Anton Lebedev <mailbox@lebster.me>

# Add crontab file in the cron directory
COPY test.sh /root/test.sh


# Give execution rights on the cron scripts
RUN chmod 0644 /root/test.sh

#Install Cron
RUN apt-get update
RUN apt-get -y install cron

# Add crontab file in the cron directory
COPY cronjob /etc/cron.d/cronjob

# Give execution rights on the cron job
RUN chmod 0644 /etc/cron.d/cronjob

# Apply cron job
RUN /usr/bin/crontab /etc/cron.d/cronjob

CMD cron && tail -f /dev/null
