# Email check

[![David](https://img.shields.io/david/pensierinmusica/email-check.svg)](https://www.npmjs.com/package/email-check)
[![npm](https://img.shields.io/npm/v/email-check.svg)](https://www.npmjs.com/package/email-check)

## Introduction

Email check is a [npm](http://npmjs.org) async module for [NodeJS](http://nodejs.org/), that **checks if an email address exists**.

It first validates the email through regex, and then pings the relative MX server.

It works with native JS promises (and needs a JS engine that supports them).

## Install

`npm install email-check`

(add "--save" if you want the module to be automatically added to your project's "package.json" dependencies)

## Usage

`emailCheck(email, [opts])`

The function signature accepts two arguments and returns a promise, eventually fulfilled with `true` if the email address exists, or `false` if it doesn't.

- `email` (string) the email address to check.
- `opts` (object) the options object.

The options object can have three properties:

- `from` (string) email address originating the request (defaults to the same value as "email").
- `host` (string) fqdn of SMTP server originating the request (defaults to an empty string).
- `timeout` (number) max allowed idle time in milliseconds (defaults to 5000).

### Example

```js
var emailCheck = require('email-check');

// Quick version
emailCheck('mail@example.com')
  .then(function (res) {
    console.log(res);
  })
  .catch(function (err) {
    console.error(err);
  });

// With custom options
emailCheck('mail@example.com', {
  from: 'address@domain.com',
  host: 'mail.domain.com',
  timeout: 3000
})
  .then(function (res) {
    console.log(res);
  })
  .catch(function (err) {
    console.error(err);
  });

```

***

MIT License