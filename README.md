# TsingYouNet

> Your One-Stop solution for a full-stack app with ES6/ES2015 React.js
 featuring universal Redux, React Router, React Router Redux Hot reloading, CSS modules, Express 4.x,
 and multiple ORMs. :rocket:


#### Demo site:


## Features:
- [**universal**](https://medium.com/@ghengeveld/isomorphism-vs-universal-javascript-4b47fb481beb#.4x2t3jlmx) Rendering
- [**Redux**](https://github.com/reactjs/redux) Predictive state containers.
- Server-side rendering with [**React Router**](https://github.com/reactjs/react-router) 2.x. Having server-side rendering allows you to pre-render the initial state of your components when a user (or search engine crawler) requests a page.
- Integrating Redux with React Router  [React Router Redux](https://github.com/reactjs/react-router-redux)
- Asynchronous Data Fetching on server-side rendering
- Server side authentication + Redirecting for components

- Hot reloading using [**react-transform-hmr**](https://github.com/gaearon/react-transform-hmr)
- Time travel using [**Redux-Devtools Chrome Extension**](https://github.com/zalmoxisus/redux-devtools-extension)
- [**Webpack**](https://github.com/webpack/webpack) for both development and production bundles. It's (in my opinion) the best bundler for JS, CSS, LESS, images, and lots more!
- [**CSS Modules**](https://github.com/css-modules/css-modules) allows for modular and reusable CSS. Say goodbye to conflicts (most of them) and global scope

- **Unit Testing** with webpack, karma, jsdom, mocha, sinon & enzyme
	- Reducers
	- Components ([Enzyme](http://airbnb.io/enzyme))
	- Synchronous and Asynchronous Actions

- Express 4.x server with a ton of middleware
- Mongoose for MongoDB
- Sequelize for Postgres
- Procfile to enable deployment to Heroku & Docs on Salt configurations + Deployment for Digital Ocean


===prep mongo db:
https://docs.mongodb.com/v3.0/tutorial/install-mongodb-on-amazon/
sudo service mongod start
sudo service mongod stop
sudo service mongod restart

log files
sudo rm -r /var/log/mongodb

data files
sudo rm -r /var/lib/mongo

==init node npm
https://gist.github.com/mathjoy/7968661d6199ffc4904aafcc0f3eff2d

sudo yum install nodejs npm --enablerepo=epel

==instance:

## Motivation

Building the SNS using best practice.

## Using Redux

The main principles of having:
- a single store
- state being read-only (you have to express an intent to mutate being creating actions)
- mutations written as pure functions

make it very fun and easy to write **predictable** code! 


Or if you are more of a *visual learner* watch the free egghead video series narrated by the creator of redux:

1. [Getting Started](https://egghead.io/series/getting-started-with-redux)
2. [Building Idiomatically](https://egghead.io/series/building-react-applications-with-idiomatic-redux)

#### Data Flow

A simplistic representation of data flow from server to client is:

```
Express app.use() receives a request
-> Calls a pre-built webpack file for the server
-> Runs matching of routes in react-router for server
-> Makes async data fetching request
-> Renders Route component to string
-> Construct HTML file (with Meta, Link tags using helmet)
-> Browser receives html file with initial state
-> Client side React.JS kicks in and initializes with given state
-> Continues where it left off
-> Everyone is happy :)
```

More TBD

#### Redux DevTools

You will have to install redux devtools extension from [here](https://github.com/zalmoxisus/redux-devtools-extension) and then everything should just work!

## Instructions

#### Database

We currently support MongoDB and Postgres, as well as the ability to not use any database. [Learn](docs/databases.md) about how to configure your app.

#### Development

Development is a breeze. Once you have installed all your dependencies all the configuration is done for you. using simple The process is outlined [here](docs/development.md).

#### Unit Tests

Testing with:
- `karma` as test runner
	- `karma.conf.js` for the main karma configuration (it has webpack configurations)
	- `tests.webpack.js` which is the single entry file. It uses `webpack`'s require API to find all the files we need that have a `-test.js` suffix.
- `mocha` as the test framework
- `jsdom` as my test environment

```bash
# Run test once
npm test

# Run in watch mode
npm test:watch
```

We have unit tests for async (redux) actions, reducers, and stateless components with [enzyme](http://airbnb.io/enzyme).

#### Deployment

Currently we support [Heroku](docs/deployment/Heroku.md) and [Digital Ocean](docs/deployment/DigitalOcean.md) and [AWS](docs/deployment/AWS.md)

#### Roadmap




## FAQ

We have assembled an FAQ [here](/docs/FAQ.md)



## How to Contribute:

Best way to keep up to date is check the TsingYouNet.
License
===============
MIT

http://iconof.com/blog/how-to-install-setup-node-js-on-amazon-aws-ec2-complete-guide/#installNode
Install Node.js and NPM on your Amazon EC2 instance

At last, it’s time to install Node.js on your Amazon Linux! We are going to install some required packages to compile Node and get Node from its Github repo. Type the following:
sudo yum install gcc-c++ make
sudo yum install openssl-devel
sudo yum install git
git clone git://github.com/nodejs/node.git
cd node

node js for redhat:
curl --silent --location https://rpm.nodesource.com/setup_6.x | bash -