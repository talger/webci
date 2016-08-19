FROM ubuntu:trusty

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && \
	apt-get upgrade -y 

RUN apt-get install -y \
        git \
        unzip \
        wget \ 
        php5-cli \ 
        php5-xdebug \
        php5-memcached \
        php5-curl && \
    rm -rf /var/lib/apt/lists/*

#RUN sed -i \
#        -e "s/^;date.timezone.*/date.timezone = Europe/Budapest" \
#        -e "s/^memory_limit.*/memory_limit = -1/" \
#        /etc/php/php.ini && \

RUN wget http://getcomposer.org/composer.phar && \
	mv composer.phar /usr/local/bin/composer && \
	chmod +x /usr/local/bin/composer && \
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