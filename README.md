This build consist my most commonly used php configuration to Symfony Framework
# Dockerfiles
[`latest`](https://github.com/IvanBinzz/php-symfony/blob/master/prod/Dockerfile)
[`dev`](https://github.com/IvanBinzz/php-symfony/blob/master/dev/Dockerfile)
#  What is difference? 
`dev` extend `latest` by adding xDebug 
# Extensions
- amqp
- bcmath
- imagick
- intl
- mbstring
- pdo
- pdo_mysql
- pdo_pgsql
- pgsql
- redis
- sockets
- zip
# ENV
- RABBITMQ_VERSION v0.8.0
- PHP_AMQP_VERSION v1.9.3
- PHP_REDIS_VERSION 3.1.4
- PHP_IMAGIC_VERSION 3.4.3
- TIMEZONE "Europe/Kiev"