FROM ruby:3.0.2-alpine

RUN gem install rubocop-rails && \
    gem install rubocop-performance && \
    gem install rubocop-rake && \
    gem install rubocop-rspec && \
    gem install rubocop-minitest && \
    gem install rubocop-packaging && \
    gem install specific_install && \
    apk add --update-cache --no-cache --virtual .install-deps git && \
    gem specific_install --location https://github.com/cumet04/rubocop-daemon --branch binding_option && \
    apk del --purge .install-deps

ENV WORKDIR /workspace
WORKDIR ${WORKDIR}
CMD ["rubocop-daemon", "start", "--no-daemon", "--binding", "0.0.0.0", "--port", "3001"]