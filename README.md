# fh-sync

Node.js implementation of the FeedHenry Data Syncronisation Server.
To be used in conjunction with the FeedHenry Data Syncronisation Client.

## Usage

```
npm install --save fh-sync
```

This will install the latest version of fh-sync and save the installed version in your package.json

To use sync in your application, require it and call `connect`.

```js
var sync = require('fh-sync');

var mongodbConnectionString = 'mongodb://127.0.0.1:27017/sync';
var redisUrl = 'redis://127.0.0.1:6379';

sync.api.connect(mongodbConnectionString, {}, redisUrl, function(){});
```

To configure a dataset for syncing, wait for the `sync:ready` event, then `init` the dataset.

```js
sync.api.getEventEmitter().on('sync:ready', function() {
  console.log('sync ready');

  sync.api.init('myDataset', {
    syncFrequency: 10 // seconds
  }, function() {});
});
```

## Tests
In order to run the tests, please make sure you have [Docker](https://www.docker.com/) installed.

Before running tests do:

```
npm install
npm install -g grunt-cli
```

Then to run the tests use ```npm test```

