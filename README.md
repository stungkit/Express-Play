# Backend Starter Kit

:truck: A boilerplate for Node.js, Express, Mongoose, Heroku, mLab, Nodemon, PM2, and Babel.

[![Build Status](https://img.shields.io/circleci/project/github/Shyam-Chen/Backend-Starter-Kit/master.svg)](https://circleci.com/gh/Shyam-Chen/Backend-Starter-Kit)
[![Coverage Status](https://img.shields.io/codecov/c/github/Shyam-Chen/Backend-Starter-Kit/master.svg)](https://codecov.io/gh/Shyam-Chen/Backend-Starter-Kit)
 //
[![Dependency Status](https://img.shields.io/david/Shyam-Chen/Backend-Starter-Kit.svg)](https://david-dm.org/Shyam-Chen/Backend-Starter-Kit)
[![devDependency Status](https://img.shields.io/david/dev/Shyam-Chen/Backend-Starter-Kit.svg)](https://david-dm.org/Shyam-Chen/Backend-Starter-Kit?type=dev)

[Live Demo](https://web-go-demo.herokuapp.com/)

This seed repository provides the following features:

* ---------- **Essentials** ----------
* [x] API routing with [**Express**](http://expressjs.com/).
* [x] Data query language with [**GraphQL**](http://graphql.org/).
* [x] Object document mapping with [**Mongoose**](http://mongoosejs.com/).
* [x] Object relational mapping with [**Sequelize**](http://docs.sequelizejs.com/).
* [x] Utility functions with [**Lodash**](https://lodash.com/).
* [x] Reactive extensions with [**ReactiveX**](http://reactivex.io/).
* [x] Authenticate requests with [**Passport**](http://passportjs.org/).
* [x] Real-time bidirectional communication with [**Socket**](https://socket.io/).
* [x] In-memory data structure store with [**Redis**](https://redis.io/).
* [x] Machine learning with [**TensorFlow**](https://js.tensorflow.org/).
* ---------- **Tools** ----------
* [x] Next generation JavaScript with [**Babel**](https://github.com/babel/babel).
* [x] JavaScript static code analyzer with [**ESLint**](https://github.com/eslint/eslint).
* [x] Type annotations with [**Flow**](https://github.com/facebook/flow).
* [x] Testing platform with [**Jest**](https://github.com/facebook/jest).
* [x] HTTP testing with [**Supertest**](https://github.com/visionmedia/supertest).
* [x] Test coverage integration with [**Codecov**](https://codecov.io/).
* [x] Automatically restart application with [**Nodemon**](https://github.com/remy/nodemon).
* [x] Keeping application alive with [**PM2**](https://github.com/Unitech/pm2).
* ---------- **Environments** ----------
* [x] Server-side platform with [**Node**](https://nodejs.org/).
* [x] Version control with [**Git**](https://github.com/git/git).
* [x] Code repository with [**GitHub**](https://github.com/).
* [x] Fast and deterministic builds with [**Yarn**](https://github.com/yarnpkg/yarn).
* [x] Cloud application hosting with [**Heroku**](https://www.heroku.com/).
* [x] Cloud NoSQL database hosting with [**mLab**](https://mlab.com/).
* [x] Cloud SQL database hosting with [**ElephantSQL**](https://www.elephantsql.com/).
* [x] Cloud Storage‎ hosting with [**Cloudinary**](https://cloudinary.com/).
* [x] Cloud memory cache hosting with [**RedisLabs**](https://redislabs.com/).
* [x] Monitoring service with [**UptimeRobot**](https://uptimerobot.com/).
* [x] Log management service with [**Papertrail**](https://papertrailapp.com/).
* [x] Performance and security with [**Cloudflare**](https://www.cloudflare.com/).
* [x] Software container with [**Docker**](https://github.com/docker/docker).
* [x] Continuous integration with [**CircleCI**](https://circleci.com/).

Here are some related seed repositories:

* ---------- **Client-side** ----------
* [Web Starter Kit](https://github.com/Shyam-Chen/Frontend-Starter-Kit) - Make for Progressive Web Apps.
* [Mobile Starter Kit](https://github.com/Shyam-Chen/Mobile-Starter-Kit) - Make for Cross-platform Mobile Apps.
* [Desktop Starter Kit](https://github.com/Shyam-Chen/Desktop-Starter-Kit) - Make for Cross-platform Desktop Apps.
* ---------- **Server-side** ----------
* [Platform Starter Kit](https://github.com/Shyam-Chen/Backend-Starter-Kit) - Make for Flexible Cloud Platform.
* [Functions Starter Kit](https://github.com/Shyam-Chen/Functions-Starter-Kit) - Make for Serverless Cloud Functions.
* [Infrastructure Starter Kit](https://github.com/Shyam-Chen/Infrastructure-Starter-Kit) - Make for Containerized Cloud Infrastructure.

## Table of Contents

* [Getting Started](#getting-started)
* [Dockerization](#dockerization)
* [Configuration](#configuration)
* [Using Libraries](#using-libraries)
* [Directory Structure](#directory-structure)

## Getting Started

Follow steps to execute this boilerplate.

1. Clone this boilerplate

```bash
$ git clone --depth 1 https://github.com/Shyam-Chen/Backend-Starter-Kit.git <PROJECT_NAME>
$ cd <PROJECT_NAME>
```

2. Install dependencies

```bash
$ yarn install && yarn typed
```

3. Start a local server

```bash
$ yarn start
```

4. Compile and bundle code

```bash
$ yarn build
```

5. Check the code quality

```bash
$ yarn lint
```

6. Run the unit tests

```bash
$ yarn test
```

7. Run the end-to-end tests

```bash
$ yarn e2e
```

## Dockerization

Dockerize an application.

1. Build and run the container in the background

```bash
$ docker-compose up -d api
```

2. Run a command in a running container

```bash
$ docker-compose exec api <COMMAND>
```

3. Remove the old container before creating the new one

```bash
$ docker-compose rm -fs
```

4. Restart up the container in the background

```bash
$ docker-compose up -d --build api
```

5. Push images to Docker Cloud

```diff
# .gitignore

  .DS_Store
  node_modules
  npm
  dist
  coverage
+ dev.Dockerfile
+ stage.Dockerfile
+ prod.Dockerfile
  *.log
```

```bash
$ docker login
$ docker build -f ./tools/<dev|stage|prod>.Dockerfile -t <IMAGE_NAME>:<IMAGE_TAG> .

# checkout
$ docker images

$ docker tag <IMAGE_NAME>:<IMAGE_TAG> <DOCKER_ID_USER>/<IMAGE_NAME>:<IMAGE_TAG>
$ docker push <DOCKER_ID_USER>/<IMAGE_NAME>:<IMAGE_TAG>

# remove
$ docker rmi <REPOSITORY>:<TAG>
# or
$ docker rmi <IMAGE_ID>
```

6. Pull images from Docker Cloud

```diff
# circle.yml

+ echo "$DOCKER_PASSWORD" | docker login -u "$DOCKER_USERNAME" --password-stdin
  docker login -u="<DOCKER_USERNAME>" -p="${HEROKU_TOKEN}" registry.heroku.com
- docker build -f ./tools/<dev|stage|prod>.Dockerfile -t registry.heroku.com/<HEROKU_PROJECT>/web .
+ docker pull <DOCKER_ID_USER>/<IMAGE_NAME>:<IMAGE_TAG>
+ docker tag <IMAGE_NAME>:<IMAGE_TAG> registry.heroku.com/<HEROKU_PROJECT>/web
  docker push registry.heroku.com/<HEROKU_PROJECT>/web
```

## Configuration

### Default environments

Set your local environment variables.

```js
// src/env.js
export const SECRET = process.env.SECRET || <PUT_YOUR_SECRET_HERE>;
export const MONGODB_URI = process.env.MONGODB_URI || <PUT_YOUR_MONGODB_URI_HERE>;
export const POSTGRES_URL = process.env.POSTGRES_URL || <PUT_YOUR_POSTGRES_URL_HERE>;
export const REDIS_PORT = process.env.REDIS_PORT || <PUT_YOUR_REDIS_PORT_HERE>;
export const REDIS_HOST = process.env.REDIS_HOST || <PUT_YOUR_REDIS_HOST_HERE>;
export const SENTRY_DSN = process.env.SENTRY_DSN || <PUT_YOUR_SENTRY_DSN_HERE>;
```

### Deployment environments

Set your deployment environment variables.

```dockerfile
# <dev|stage|prod>.Dockerfile
ENV SECRET <PUT_YOUR_SECRET_HERE>
ENV MONGODB_URI <PUT_YOUR_MONGODB_URI>
ENV POSTGRES_URL <PUT_YOUR_POSTGRES_URL_HERE>
ENV REDIS_PORT <PUT_YOUR_REDIS_PORT_HERE>
ENV REDIS_HOST <PUT_YOUR_REDIS_HOST_HERE>
ENV SENTRY_DSN <PUT_YOUR_SENTRY_DSN_HERE>
```

## Using Libraries

1. Example of REST

```js
import { Router } from 'express';

import document from '~/document';

const router = Router();

router.get('/', async (req, res, next) => {
  try {
    const data = await document.List.find({}).exec();
    res.json(data);
  } catch (err) {
    next(err);
  }
});

export default router;
```

2. Example of GraphQL

```js
import gql from 'graphql-tag';

import document from '~/document';

export const listTypeDefs = gql`
  type List {
    _id: ID!
    text: String!
  }

  type Query {
    list: [List]
  }
`;

export const listResolvers = {
  Query: {
    async list(root, { text }) {
      try {
        const data = await document.List.find({}).exec();
        return data;
      } catch (err) {
        console.error(err);
      }
    }
  }
};
```

3. Example of Document

```js
import mongoose, { Schema } from 'mongoose';

const listSchema = Schema({
  text: String,
});

export const List = mongoose.model('List', listSchema);
```

4. Example of Relational

```js
export default (sequelize, DataTypes) => {
  const List = sequelize.define('List', {
    text: DataTypes.STRING
  });

  return List;
};
```

5. Example of Lodash

```js
import { of } from 'rxjs';
import { lowerFirst, pad } from 'lodash';

of(lowerFirst('Hello'), pad('World', 5))
  .subscribe(value => console.log(value));
  // hello
  // World
```

6. Example of ReactiveX

```js
import { timer, of } from 'rxjs';
import { mapTo, combineAll } from 'rxjs/operators';

timer(2000)
  .pipe(
    mapTo(of('Hello', 'World')),
    combineAll(),
  )
  .subscribe(value => console.log(value));
  // ["Hello"]
  // ["World"]
```

7. Example of Socket

```js
import { io } from '~/core/socket';

io.emit('A', { foo: 'bar' });
io.on('B', data => console.log(data));  // { foo: 'baz' }
```

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/2.0.1/socket.io.js"></script>
<script>
const socket = io();

socket.on('connect', () => console.log('WS: Accept a connection.'));

socket.on('A', data => {
  console.log(data);  // { foo: 'bar' }
  socket.emit('B', { foo: 'baz' });
});
</script>
```

8. Example of Redis

```js
import { client } from '~/core/redis';

client.hmset('thing', {
  foo: 'js',
  bar: 'html',
  baz: 'css'
});

client.hgetall('thing', (err, object) => {
  console.log(object);
});
```

## Directory Structure

```coffee
.
├── src
│   ├── core  -> core feature module
│   ├── document  -> mongodb models
│   ├── graphql  -> query language
│   ├── relational  ->  postgresql models
│   ├── rest  -> restful api
│   ├── shared  -> shared feature module
│   ├── api.js
│   └── env.js
├── tools
│   └── ...
├── .babelrc
├── .editorconfig
├── .eslintrc
├── .flowconfig
├── .gitignore
├── Dockerfile
├── LICENSE
├── README.md
├── circle.yml
├── docker-compose.yml
├── jest.config.js
├── package.json
├── processes.js
└── yarn.lock
```
