FROM maven:3.9.6-eclipse-temurin-18

# Google Chrome

ARG CHROME_VERSION=124.0.6367.91-1
RUN apt-get update -qqy \
	&& apt-get -qqy install gpg unzip \
	&& wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
	&& echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
	&& apt-get update -qqy \
	&& apt-get -qqy install google-chrome-stable=$CHROME_VERSION \
	&& rm /etc/apt/sources.list.d/google-chrome.list \
	&& rm -rf /var/lib/apt/lists/* /var/cache/apt/* \
	&& sed -i 's/"$HERE\/chrome"/"$HERE\/chrome" --no-sandbox/g' /opt/google/chrome/google-chrome

# ChromeDriver

ARG CHROME_DRIVER_VERSION=124.0.6367.91
RUN wget -q -O /tmp/chromedriver.zip https://storage.googleapis.com/chrome-for-testing-public/$CHROME_DRIVER_VERSION/linux64/chromedriver-linux64.zip \
	&& unzip /tmp/chromedriver.zip -d /opt \
	&& rm /tmp/chromedriver.zip \
	&& ln -s /opt/chromedriver-linux64/chromedriver /usr/bin/chromedriver
