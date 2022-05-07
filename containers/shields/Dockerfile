# FROM alpine:3 as intermediate
FROM node:16
# as intermediate

# LABEL stage=intermediate

# RUN apk add --update git
RUN git clone --depth 1 --branch server-2022-05-03 https://github.com/badges/shields.git

WORKDIR /shields

RUN npm ci
# RUN node server 8080
# RUN npm run build

ENTRYPOINT ["node", "server", "8080"]

# WORKDIR /shields/public

# RUN npm i -g http-server
# ENTRYPOINT ["http-server"]

# FROM node:18

# COPY --from=intermediate /shields /shields

# WORKDIR /shields

# RUN npm ci
# RUN npm start

# ENTRYPOINT ["npm", "run", "start", "--", "-p", "8080"]