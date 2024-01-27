FROM maven:3.8-openjdk-18
COPY docker/google-chrome.repo /etc/yum.repos.d/google-chrome.repo
RUN set -eux \
    && microdnf install wget --assumeyes -y \
    && wget https://dl.google.com/linux/linux_signing_key.pub \
    && rpm --import linux_signing_key.pub \
    && microdnf install google-chrome-stable --assumeyes -y
