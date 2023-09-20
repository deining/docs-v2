---
title: Install the InfluxDB v2 JavaScript client library
description: >
  Install the Node.js JavaScript client library to write data to an InfluxDB Clustered database.
menu:
  influxdb_clustered:
    name: Install
    parent: Node.js
influxdb/clustered/tags: [client libraries, JavaScript]
weight: 100
aliases:
  - /influxdb/clustered/reference/api/client-libraries/nodejs/install
---

{{% note %}}

Install the Node.js JavaScript client library to write data to an {{% product-name %}} database.

### Tools to execute queries

InfluxDB v2 client libraries use the InfluxDB API `/api/v2/query` endpoint.
This endpoint can't query an {{% product-name %}} database.

{{% product-name %}} supports many different tools for querying data, including:

- [InfluxDB v3 client libraries](/influxdb/clustered/reference/client-libraries/v3/)
- [Flight clients](/influxdb/clustered/reference/client-libraries/flight-sql/)
- [Superset](/influxdb/clustered/query-data/sql/execute-queries/superset/)
- [Grafana](/influxdb/clustered/query-data/sql/execute-queries/grafana/)
- [InfluxQL with InfluxDB v1 HTTP API](/influxdb/clustered/primers/api/v1/#query-using-the-v1-api)
- [Chronograf](/chronograf/v1/)

{{% /note %}}

## Install Node.js

1. Install [Node.js](https://nodejs.org/en/download/package-manager/).

2. Ensure that InfluxDB is running and you can connect to it.
   For information about what URL to use to connect to your {{% product-name omit=" Clustered" %}} cluster, contact your InfluxData account representative.

3. In your terminal, create a directory for your Node.js project and change to it.

   ```sh
   mkdir influx-node-app && cd $_
   ```

4. Enter the following command to generate an npm package for your project. 
   The `npm` package manager is included with Node.js.

   ```sh
   npm init -y
   ```

## Install TypeScript

Many of the client library examples use [TypeScript](https://www.typescriptlang.org/).
Follow these steps to initialize the TypeScript project:

1. Install TypeScript and type definitions for Node.js.

   ```sh
   npm i -g typescript && npm i --save-dev @types/node
   ```
2. Create a TypeScript configuration with default values.

   ```sh
   tsc --init
   ```
3. Run the TypeScript compiler. To recompile your code automatically as you make changes, pass the `watch` flag to the compiler.

   ```sh
   tsc -w -p
   ```

## Install dependencies

Use the `@influxdata/influxdb-client` JavaScript client library to write data in {{% product-name %}}.

Open a new terminal window and install the `@influxdata/influxdb-client` package for querying and writing data:

   ```sh
   npm i --save @influxdata/influxdb-client
   ```

The `@influxdata/influxdb-client-apis` client library package won't work with {{% product-name %}}.
It only works with InfluxDB v2 management APIs.

## Configure credentials

The client examples include an [`env`](https://github.com/influxdata/influxdb-client-js/blob/master/examples/env.js) module for accessing your InfluxDB properties from environment variables or from `env.js`.
The examples use these properties to interact with the InfluxDB API.

Set environment variables or update `env.js` with your InfluxDB [database](/influxdb/clustered/admin/databases/), organization (required, but ignored), [token](/influxdb/clustered/admin/tokens/), and cluster URL.

   ```sh
   export INFLUX_URL=https://{{< influxdb/host >}}
   export INFLUX_TOKEN=DATABASE_TOKEN
   export INFLUX_ORG=ORG_ID
   export INFLUX_DATABASE=DATABASE_NAME
   ```
   Replace the following:
   - **`DATABASE_TOKEN`**: InfluxDB database token
   - **`ORG_ID`**: An arbitrary string (InfluxDB ignores this credential, but the client library requires it)
   - **`DATABASE_NAME`**: InfluxDB database name

## Next steps

Once you've installed the client library and configured credentials, you're ready to [write data](/influxdb/clustered/reference/client-libraries/v2/javascript/nodejs/write/) to InfluxDB.

{{< page-nav next="/influxdb/clustered/reference/client-libraries/v2/javascript/nodejs/write/" keepTab=true >}}