FROM ruby

LABEL name=ft-rails

# Update and install rails

RUN apt-get -y update && apt-get -y upgrade && \
	apt-get -y install nodejs && \
	gem install rails

# install rails stuff

ONBUILD COPY		. /opt/app
ONBUILD WORKDIR		/opt/app
ONBUILD RUN			bundle install
ONBUILD RUN			rake db:migrate
ONBUILD RUN			rake db:seed

ONBUILD EXPOSE 3000
