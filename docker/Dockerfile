FROM --platform=$BUILDPLATFORM alpine
ARG LINK
ARG TARGETPLATFORM
COPY ./setup.sh /setup.sh
RUN /setup.sh

FROM node:18.16.0-bullseye
COPY --from=0 /boilerplate.zip /boilerplate.zip
COPY ./entrypoint.sh /
# RUN apk add --no-cache chromium nss freetype harfbuzz ca-certificates ttf-freefont font-noto-cjk
# RUN apk add --no-cache build-base g++ cairo-dev pango-dev giflib-dev librsvg-dev
RUN apt-get update
RUN apt-get install chromium libnss3 	libfreetype-dev libharfbuzz-dev ca-certificates fonts-freefont-ttf fonts-noto-cjk
RUN apt-get install build-essential libcairo2-dev libpango1.0-dev libjpeg-dev libgif-dev librsvg2-dev
VOLUME ["/koishi"]
WORKDIR "/koishi"
ENTRYPOINT ["/entrypoint.sh"]
CMD ["yarn", "start"]
