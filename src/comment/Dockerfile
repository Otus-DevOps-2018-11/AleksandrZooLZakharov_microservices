FROM ruby:2.2
RUN echo 'deb http://cdn-fastly.deb.debian.org/debian oldstable main' > etc/apt/sources.list && echo 'deb http://cdn-fastly.deb.debian.org/debian proposed-updates main' >> etc/apt/sources.list && apt-get update -qq && apt-get install -y build-essential --no-install-recommends && apt-get autoremove && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV APP_HOME /app
RUN mkdir $APP_HOME
WORKDIR $APP_HOME

COPY Gemfile* $APP_HOME/
RUN bundle install
COPY . $APP_HOME

ENV COMMENT_DATABASE_HOST comment_db
ENV COMMENT_DATABASE comments

CMD ["puma"]
