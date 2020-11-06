FROM centos:7.4.1708

RUN yum -y update

# リポジトリ epel, remi
RUN yum -y install epel-release
RUN yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

# apacheやphpをインストール
RUN yum -y install httpd
RUN yum -y install --enablerepo=remi,remi-php72 php php-mbstring php-mysqlnd php-pdo php-cli php-common php-devel php-fpm php-gd php-pear php-pecl php-apcu php-xml php-xmlrpc
RUN yum -y install zip unzip

# xdebugをインストール
RUN yum -y install make
RUN pecl install xdebug 
# RUN docker-php-ext-enable xdebug

#npmをインストール
RUN curl -sL https://rpm.nodesource.com/setup_12.x | bash - 
RUN yum install -y nodejs


# composerをインストール
RUN cd /usr/bin \
&& curl -s http://getcomposer.org/installer | php \ 
&& ln -s /usr/bin/composer.phar /usr/bin/composer

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]

WORKDIR /var/www/html