FROM node:14.2-alpine as node
FROM nginx:1.18-alpine
SHELL ["/bin/ash", "-oeux", "pipefail", "-c"]

ENV TZ Asia/Tokyo
#ENV DOCUMENT_ROOT ${DOCUMENT_ROOT}
#ENV WEB_HOST_NAME ${WEB_HOST_NAME}
ARG DOCUMENT_ROOT
ARG WEB_HOST_NAME


RUN apk update && \
  apk add --update --no-cache --virtual=.build-dependencies g++

COPY --from=node /usr/local/bin /usr/local/bin
COPY --from=node /opt /opt
COPY ./default.conf /etc/nginx/conf.d/default.conf
RUN sed -ri -e "s!ENV_DOCUMENT_ROOT!`echo $DOCUMENT_ROOT`!g" /etc/nginx/conf.d/default.conf
RUN sed -ri -e "s!ENV_WEB_HOST_NAME!`echo $WEB_HOST_NAME`!g" /etc/nginx/conf.d/default.conf

WORKDIR /work/backend
