FROM ruby:3.1

RUN apt update -qq && apt install -y postgresql-client
WORKDIR /usr/src/app
COPY Gemfile $WORKDIR
COPY Gemfile.lock $WORKDIR

ARG RUBYGEMS_VERSION=3.3.20

RUN gem update --system $RUBYGEMS_VERSION && \
    bundle install

COPY . $WORKDIR

COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

EXPOSE 3000

CMD ["rails", "server", "-b", "0.0.0.0"]