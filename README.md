[![Travis](https://img.shields.io/travis/timbrandin/i18next-service-backend/master.svg?style=flat-square)](https://travis-ci.org/timbrandin/i18next-service-backend)
[![npm version](https://img.shields.io/npm/v/i18next-service-backend.svg?style=flat-square)](https://www.npmjs.com/package/i18next-service-backend)
[![David](https://img.shields.io/david/timbrandin/i18next-service-backend.svg?style=flat-square)](https://david-dm.org/timbrandin/i18next-service-backend)

This is an i18next backend to be used for external services, such as [spacetranslate](https://spacetranslate.com) or [locize](https://locize.com). It will load resources from the external server using xhr.

It will allow you to save missing keys containing both **default value** and **context information** by calling:

```js
i18next.t(key, defaultValue, tDescription);
i18next.t(key, { defaultValue, tDescription });
```

# Getting started

Source can be loaded via [npm](https://www.npmjs.com/package/i18next-service-backend), bower or [downloaded](https://cdn.rawgit.com/timbrandin/i18next-service-backend/master/i18next-service-backend.min.js) from this repo.

```
# npm package
$ npm install i18next-service-backend

# bower
$ bower install i18next-service-backend
```

Wiring up:

```js
import i18next from 'i18next';
import Backend from 'i18next-service-backend';

i18next
  .use(Backend)
  .init(i18nextOptions);
```

- As with all modules you can either pass the constructor function (class) to the i18next.use or a concrete instance.
- If you don't use a module loader it will be added to `window.i18nextBackendBackend`


## Backend Options

```js
{
  service: '[SERVICE_URL]', // i.e. https://api.spacetranslate.com or https://api.locize.com

  // the id of your backend project
  projectId: '[PROJECTID]',

  // add an api key if you want to send missing keys
  apiKey: '[APIKEY]',

  // the reference language of your project
  referenceLng: '[LNG]',

  // version - defaults to latest
  version: '[VERSION]'
}
```

Options can be passed in:

**preferred** - by setting options.backend in i18next.init:

```js
import i18next from 'i18next';
import Backend from 'i18next-service-backend';

i18next
  .use(Backend)
  .init({
    backend: options
  });
```

on construction:

```js
  import Backend from 'i18next-service-backend';
  const Backend = new Backend(null, options);
```

via calling init:

```js
  import Backend from 'i18next-service-backend';
  const Backend = new Backend();
  Backend.init(null, options);
```
