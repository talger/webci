FROM ubuntu:trusty

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y \
        git \
        curl \
        unzip \
        build-essential \
        wget \ 
        php5-cli \ 
        php5-xdebug \
        php5-memcached \
	php5-ldap \
        php5-curl && \
    rm -rf /var/lib/apt/lists/* && \
    curl http://getcomposer.org/composer.phar -o /usr/local/bin/composer && \
	chmod +x /usr/local/bin/composer && \
	curl http://get.sensiolabs.org/melody.phar -o /usr/local/bin/melody && \
	chmod a+x /usr/local/bin/melody && \
    useradd user && \
	mkdir -p /home/user/.bin && \
	chown -R user: /home/user
	
USER user
WORKDIR /home/user

ENV PATH /home/user/.bin:$PATH

RUN wget https://gist.githubusercontent.com/talger/faba3c7b8cc0fc4cd1ce49b7d7624343/raw/9fd86ef5b8e455b046049fe686a2f7595875e5d2/composer && \
	mv composer /home/user/.bin/composer && \
	chmod +x /home/user/.bin/composer && \
	composer config --global secure-http false && \
	composer global require "hirak/prestissimo:^0.3"
