---
title: Client Initialization
sidebar_label: Initialization
sidebar_position: 2
slug: /client-initialization/
---

Once you have [installed](client-installation.md) the Socket.IO client library, you can now init the client. The complete list of options can be found [here](../../client-options.md).

In the examples below, the `io` object comes either from:

- the `<script>` import

```html
<script src="/socket.io/socket.io.js"></script>
```

- NPM

```js
// ES6 import or TypeScript
import { io } from "socket.io-client";
// CommonJS
const io = require("socket.io-client");
```

## From the same domain

If your front is served on the same domain as your server, you can simply use:

```js
const socket = io();
```

The server URL will be deduced from the [window.location](https://developer.mozilla.org/en-US/docs/Web/API/Window/location) object.

## From a different domain

In case your front is not served from the same domain as your server, you have to pass the URL of your server.

```js
const socket = io("https://server-domain.com");
```

In that case, please make sure to enable [Cross-Origin Resource Sharing (CORS)](../02-Server/handling-cors.md) on the server.

Note: You can use either `https` or `wss` (respectively, `http` or `ws`).

```js
// the following forms are similar
const socket = io("https://server-domain.com");
const socket = io("wss://server-domain.com");
const socket = io("server-domain.com"); // only in the browser when the page is served over https (will not work in Node.js)
```

## Custom namespace

In the examples above, the client will connect to the main namespace. Using only the main namespace should be sufficient for most use cases, but you can specify the namespace with:

```js
// same origin version
const socket = io("/admin");
// cross origin version
const socket = io("https://server-domain.com/admin");
```

You can find more details about namespaces [here](../06-Advanced/namespaces.md).

## Options

The complete list of available options can be found [here](../../client-options.md).
