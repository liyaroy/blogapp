FROM ruby:2.6.5

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs

RUN mkdir /webapp

WORKDIR /webapp

ADD Gemfile /webapp/Gemfile
ADD Gemfile.lock /webapp/Gemfile.lock


WORKDIR /webapp

RUN gem install bundler
RUN bundle update --bundler
RUN bundle install
ADD . /webapp

RUN RAILS_ENV=production bundle exec rake assets:precompile
