FROM ruby:2.5

# install dependencies
RUN gem install \
        bundler \
        rubyzip \
        rack \
        puma \
        rake          `#optional` \
        mechanize     `#optional` \
        activesupport `#optional` \
        jwt           `#optional`

# create src directory to store action files
RUN mkdir -p /action/src
ADD rackapp /action/rackapp/
COPY config.ru /action

# run webserver
RUN cd /action
EXPOSE 8080
ENV BUNDLE_GEMFILE /action/src/Gemfile
ENV RUBYOPT -EUTF-8
CMD [ "puma", "/action/config.ru", "-b", "tcp://0.0.0.0:8080" ]
