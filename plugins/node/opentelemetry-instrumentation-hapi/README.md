# OpenTelemetry Hapi Instrumentation for Node.js

[![NPM Published Version][npm-img]][npm-url]
[![dependencies][dependencies-image]][dependencies-url]
[![devDependencies][devDependencies-image]][devDependencies-url]
[![Apache License][license-image]][license-image]

This module provides automatic instrumentation for the [Hapi Framework](https://hapi.dev)(`@hapi/hapi` package).

For automatic instrumentation see the
[@opentelemetry/sdk-trace-node](https://github.com/open-telemetry/opentelemetry-js/tree/main/packages/opentelemetry-node) package.

Compatible with OpenTelemetry JS API and SDK `1.0+`.

## Installation

```bash
npm install --save @opentelemetry/instrumentation-hapi
```

### Supported Versions

- `>=17.0.0 <21`

## Usage

OpenTelemetry Hapi Instrumentation allows the user to automatically collect trace data and export them to their backend of choice, to give observability to distributed systems.

To load a specific instrumentation (Hapi in this case), specify it in the registerInstrumentations' configuration.

```js
const { NodeTracerProvider } = require('@opentelemetry/sdk-trace-node');
const { registerInstrumentations } = require('@opentelemetry/instrumentation');
const { HapiInstrumentation } = require('@opentelemetry/instrumentation-hapi');

const provider = new NodeTracerProvider();
provider.register();

registerInstrumentations({
  instrumentations: [
    new HapiInstrumentation(),
  ],
});
```

If instead you would just want to load a specific instrumentation only (**hapi** in this case);

```js
const { NodeTracerProvider } = require('@opentelemetry/sdk-trace-node');
const { HapiInstrumentation } = require('@opentelemetry/instrumentation-hapi');
const provider = new NodeTracerProvider();
provider.register();

const hapiInstrumentation = new HapiInstrumentation();
hapiInstrumentation.setTracerProvider(provider);
```

See [examples/hapi](https://github.com/open-telemetry/opentelemetry-js-contrib/tree/main/examples/hapi) for a short example using Hapi

<!-- 
The dev dependency of `@hapi/podium@4.1.1` is required to force the compatible type declarations. See: https://github.com/hapijs/hapi/issues/4240
-->

## Hapi Instrumentation Support

This package provides automatic tracing for hapi server routes and [request lifecycle](https://github.com/hapijs/hapi/blob/main/API.md#request-lifecycle) extensions defined either directly or via a Hapi plugin.

## Useful links

- For more information on OpenTelemetry, visit: <https://opentelemetry.io/>
- For more about OpenTelemetry JavaScript: <https://github.com/open-telemetry/opentelemetry-js>
- For help or feedback on this project, join us in [GitHub Discussions][discussions-url]

## License

Apache 2.0 - See [LICENSE][license-url] for more information.

[discussions-url]: https://github.com/open-telemetry/opentelemetry-js/discussions
[license-url]: https://github.com/open-telemetry/opentelemetry-js-contrib/blob/main/LICENSE
[license-image]: https://img.shields.io/badge/license-Apache_2.0-green.svg?style=flat
[dependencies-image]: https://status.david-dm.org/gh/open-telemetry/opentelemetry-js-contrib.svg?path=plugins%2Fnode%2Fopentelemetry-instrumentation-hapi
[dependencies-url]: https://david-dm.org/open-telemetry/opentelemetry-js-contrib?path=plugins%2Fnode%2Fopentelemetry-instrumentation-hapi
[devDependencies-image]: https://status.david-dm.org/gh/open-telemetry/opentelemetry-js-contrib.svg?path=plugins%2Fnode%2Fopentelemetry-instrumentation-hapi&type=dev
[devDependencies-url]: https://david-dm.org/open-telemetry/opentelemetry-js-contrib?path=plugins%2Fnode%2Fopentelemetry-instrumentation-hapi&type=dev
[npm-url]: https://www.npmjs.com/package/@opentelemetry/instrumentation-hapi
[npm-img]: https://badge.fury.io/js/%40opentelemetry%2Finstrumentation-hapi.svg
