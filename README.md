# Dockerized Laravel 8
This is a template project for quickly getting started with developing Laravel 8 projects.

This makes use of Ubuntu 20.04 as the base image as it is easy enough to tweak and extend for a broader audience. E.g.
I am guessing more people know how to configure Ubuntu than Alpine Linux.


## Getting Started

1. Create an `.env` file from the `.env.example` file and fill it in.
1. Build the Docker image by running `docker-compose build`
1. Run the site by running `docker-compose up -d`
    * When devving, run `docker-compose -f docker-dev-compose.yml` to run with a volume for the site so that website
changes can be seen in real-time.


## Services

### Supervisor
This image comes with [Supervisor](http://supervisord.org/) installed. You can easily [configure this to manage your
Laravel queu](https://blog.programster.org/getting-started-with-laravel-queues-and-background-jobs) as well as managing
any custom processes you wish to add.


### Cron
This image comes with the cron service, which is also used as the foreground process for the container to keep it
running. Use the cron service when you wish for a script to run at a certain point in time. For everything else, I would
advise using [Supervisor](http://supervisord.org/).


## Extra Info

### HTTPS / SSL
There are a million different ways to configure SSL so there is no point in me implementing one of them in this template.
For simplicity, I would create create an `ssl` volume at the top level, and tweak your apapche configuration to make use
of it as well as adding `RUN a2enmod ssl` to the Dockerfile, but you may wish to
[use a reverse proxy](https://blog.programster.org/jwilder-reverse-proxy-with-wildcard-ssl) or have something set up with
AWS etc.