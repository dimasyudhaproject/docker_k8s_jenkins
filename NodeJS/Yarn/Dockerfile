#
# Copyright (C) 2022 Dimas Yudha Pratama <fsdimasyudha@gmail.com>
#
FROM node:18.12.1-alpine3.16
RUN addgroup --gid 10001 \
             --system dimas \
    && adduser  --uid 10000 \
                --system \
                --ingroup dimas \
                --home /home/dimasyudha yudha \
    && apk add --no-cache tini \
                       bind-tools
USER yudha
WORKDIR /home/dimasyudha
COPY package.json yarn.lock ./
RUN yarn install --frozen-lockfile
COPY . .
ENTRYPOINT ["/sbin/tini", "--"]
CMD ["yarn", "start"]