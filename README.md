<h1 align="center">expresso-gateway</h1>
<h3 align="center">( Express Gateway TypeScript )</h3>
<br/>

[![version](https://img.shields.io/badge/version-2.1.0-blue.svg?cacheSeconds=2592000)](https://github.com/masb0ymas/expresso-gateway/releases/tag/v2.1.0)
[![Node](https://img.shields.io/badge/Node-12.18.0-informational?logo=node.js&color=43853D)](https://nodejs.org/docs/latest-v12.x/api/index.html)
[![TypeScript](https://img.shields.io/badge/Typescript-4.4.3-informational?logo=typescript&color=2F74C0)](https://www.typescriptlang.org/)
[![Express](https://img.shields.io/badge/Express-4.17.1-informational?logo=express&color=B1B1B1)](https://expressjs.com/)
[![documentation](https://img.shields.io/badge/documentation-yes-brightgreen.svg)](https://github.com/masb0ymas/expresso-gateway#readme)
[![maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/masb0ymas/expresso-gateway/graphs/commit-activity)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/masb0ymas/expresso-gateway/blob/master/LICENSE.md)

> Just Boilerplate Express with TypeScript ( 🦊 )

## Prerequisites

- npm >= `v6.x`
- node >= `v12.x`
- eslint `v7.x`
- husky >= `v7.x`
- Familiar with TypeScript 💪

## Feature

- [TypeScript](https://github.com/microsoft/TypeScript) `v4.x`
- [Nodemailer](https://github.com/nodemailer/nodemailer)
- [Handlebars](https://github.com/wycats/handlebars.js) for templating HTML
- [Yup](https://github.com/jquense/yup) for validation schema
- JavaScript Style [Standard with TypeScript](https://github.com/standard/eslint-config-standard-with-typescript)
- Formating code using [Prettier](https://github.com/prettier/prettier) Integration [Eslint](https://github.com/prettier/eslint-config-prettier) and [TypeScript Eslint](https://github.com/typescript-eslint/typescript-eslint#readme)
- Using [Module Alias](https://github.com/ilearnio/module-alias) for simplify the require/import paths
- Documentation with [Swagger](https://github.com/swagger-api/swagger-ui)
- Generate Log File with [Winston](https://github.com/winstonjs/winston)
- [Convensional Commit](https://www.conventionalcommits.org/en/v1.0.0/) with [Husky](https://github.com/typicode/husky) & [Commitlint](https://github.com/conventional-changelog/commitlint)

## How to use

clone this repo with `https` / `ssh` / `github cli`

```sh
git clone https://github.com/masb0ymas/expresso-gateway.git
```

After cloning this repo, make sure you have `duplicated` the `.env.example` file to `.env`, don't let the .env.example file be deleted or renamed.

## Install

```sh
npm install

or

yarn
```

## Enabled Husky

```sh
npx husky install

or

yarn husky install
```

## Generate Secret Key

```sh
npm run key:generate

or

yarn key:generate
```

## Usage Development

```sh
npm run dev

or

yarn dev
```

## Type Check

```sh
npm run test:types

or

yarn test:types
```

## Type Check Watch mode

```sh
npm run test:types-watch

or

yarn test:types-watch
```

## Build

```sh
npm run build

or

yarn build
```

## Usage Production

```sh
npm run serve:production

or

yarn serve:production
```

## Usage PM2 for Cluster Process

```sh
pm2 start ecosystem.config.js --env=production
```

## Config Nginx for Limiter / Node JS

```sh
server {
	listen 80;
	listen [::]:80;

	server_name yourdomain.com;
	client_max_body_size 2000M;
	location / {
	proxy_pass http://127.0.0.1:7000;
	proxy_http_version 1.1;
	proxy_set_header Upgrade $http_upgrade;
	proxy_set_header Connection 'upgrade';
	proxy_set_header Host $host;
	proxy_set_header X-Real-IP $remote_addr;
	proxy_set_header X-Forwarded-Proto $scheme;
	proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
	proxy_cache_bypass $http_upgrade;
	}
}
```

## Run loadtest

```sh
npm install -g loadtest
```

Then run the app that you want to test with `node app.js`. We’ll start by testing the version that doesn’t use clustering.

With the app running, open another Terminal and run the following load test:

```sh
loadtest http://localhost:8000/v1/user -n 1000 -c 100
```

`-n` = network / requests

`-c` = concurrency

`--rps` = request per second

Read documentation [loadtest](https://www.npmjs.com/package/loadtest)

## Result loadtest:

if you want to try `1000 requests` you have to increase `RATE_LIMIT=1000`, by default `100 requests`

```sh
Requests: 0 (0%), requests per second: 0, mean latency: 0 ms

Target URL:          http://localhost:8000/v1/user
Max requests:        1000
Concurrency level:   100
Agent:               none

Completed requests:  1000
Total errors:        0
Total time:          1.7057602980000002 s
Requests per second: 586
Mean latency:        162.8 ms

Percentage of the requests served within a certain time
  50%      136 ms
  90%      261 ms
  95%      337 ms
  99%      390 ms
 100%      419 ms (longest request)
```

## Run tests

```sh
npm run test

or

yarn test
```

## Run with Docker

Adjust the config in .env like this:

```sh
PORT=8000 # change this port according to your needs
```

## Release your version app

if you want to release the app version, you can use the following command :

```sh
npm run release

or

yarn release
```

## SMTP Basic

I use [topol.io](https://topol.io/) to create email templates, and it's free and can export to html format

```sh
MAIL_DRIVER=smtp
MAIL_HOST=smtp.mailgun.org
MAIL_PORT=465
MAIL_AUTH_TYPE=
MAIL_USERNAME=your_mail@domain.com
MAIL_PASSWORD=your_password
MAIL_ENCRYPTION=
```

## SMTP with Mailgun API

```sh
MAILGUN_API_KEY=your_api_key_mailgun
MAILGUN_DOMAIN=your_domain
```

## SMTP Google Oauth Email ( Gmail )

```sh
MAIL_DRIVER=gmail
MAIL_HOST=
MAIL_PORT=
MAIL_AUTH_TYPE=OAuth2
MAIL_USERNAME=your_account@gmail.com
MAIL_PASSWORD=
MAIL_ENCRYPTION=

OAUTH_CLIENT_ID=your_client_id
OAUTH_CLIENT_SECRET=your_client_secret
OAUTH_REDIRECT_URL=https://developers.google.com/oauthplayground
OAUTH_REFRESH_TOKEN=your_refresh_token
```

[Setup Google Oauth](https://medium.com/@nickroach_50526/sending-emails-with-node-js-using-smtp-gmail-and-oauth2-316fe9c790a1)

## Author

👤 **masb0ymas**

- Website: https://resume.masb0ymas.vercel.app
- Twitter: [@masb0ymas](https://twitter.com/masb0ymas)
- Github: [@masb0ymas](https://github.com/masb0ymas)
- LinkedIn: [@masb0ymas](https://www.linkedin.com/in/masb0ymas/)

## Support Me

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/I2I03MVAI)

[<img height="40" src="https://trakteer.id/images/mix/navbar-logo-lite.png">](https://trakteer.id/masb0ymas)

## Show your support

Give a ⭐️ if this project helped you!

---

_This README was generated with ❤️ by [readme-md-generator](https://github.com/kefranabg/readme-md-generator)_
