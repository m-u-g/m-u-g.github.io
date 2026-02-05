FROM ruby:3.2-alpine

RUN apk add --no-cache \
    build-base \
    libstdc++ \
    git \
    gcompat

RUN gem install bundler jekyll

WORKDIR /workspace

CMD ["sh"]