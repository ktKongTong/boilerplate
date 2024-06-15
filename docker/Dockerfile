FROM --platform=$BUILDPLATFORM alpine
ARG LINK
ARG TARGETPLATFORM
COPY ./setup.sh /setup.sh
RUN /setup.sh

FROM node:lts-alpine
COPY --from=0 /boilerplate.zip /boilerplate.zip
COPY ./entrypoint.sh /
RUN apk add --no-cache chromium nss freetype harfbuzz ca-certificates ttf-freefont font-noto-cjk
RUN apk add --no-cache build-base g++ cairo-dev pango-dev giflib-dev librsvg-dev jpeg-dev
RUN /entrypoint.sh

RUN cd /koishi && yarn add canvas

VOLUME ["/koishi"]
WORKDIR "/koishi"
# ENTRYPOINT ["/entrypoint.sh"]
CMD ["yarn", "start"]
