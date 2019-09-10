FROM ruby

RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y build-essential sqlite3 nodejs yarn

ONBUILD COPY app /opt/app
ONBUILD WORKDIR /opt/app

RUN gem install rails

ONBUILD EXPOSE 3000
ONBUILD RUN bundle install
ONBUILD RUN bundle exec rake db:migrate
ONBUILD RUN rake db:seed

