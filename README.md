<div align="center">
  <h1>
      Package forked from bunyan-gelf
  </h1>
</div>

Bunyan stream to send logs in GELF format to GELF related log collecting services).

## Installation

With yarn:

```
yarn add @medinamarquezp/bunyangelf
```

With npm:

```
npm install @medinamarquezp/bunyangelf
```

## Example

For more information about bunyan streams read the official bunyan [documentation](https://github.com/trentm/node-bunyan#streams).

```javascript
const bunyan = require("bunyan");
const BunyanToGelfStream = require("@medinamarquezp/bunyangelf");

const streams = [
  {
    type: "raw",
    stream: new BunyanToGelfStream({
      host: "log-service.example", // GELF related service url (without any protocol)
      port: 9999,
      protocol: "tcp", // Supported: 'tcp' and 'udp' (default: 'udp')
    }),
  },
];

const Logger = bunyan.createLogger({
  name: "myapp",
  streams,
  serializers: bunyan.stdSerializers,
});

module.exports = Logger;
```
