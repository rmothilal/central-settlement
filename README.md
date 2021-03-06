# central-settlements
[![Git Commit](https://img.shields.io/github/last-commit/mojaloop/central-settlement.svg?style=flat)](https://github.com/mojaloop/central-settlement/commits/master)
[![Git Releases](https://img.shields.io/github/release/mojaloop/central-settlement.svg?style=flat)](https://github.com/mojaloop/central-settlement/releases)
[![Docker pulls](https://img.shields.io/docker/pulls/mojaloop/central-settlement.svg?style=flat)](https://hub.docker.com/r/mojaloop/central-settlement)
[![CircleCI](https://circleci.com/gh/mojaloop/central-settlement.svg?style=svg)](https://circleci.com/gh/mojaloop/central-settlement)


The Central Settlements service is part of the Mojaloop project and deployment.

The central settlements service exposes Settlement API to manage the settlements between FSPs and the Central Hub.
The service manages Settlement Windows and Settlements Event Triggers and provides information about FSPs accounts and settlements.

Contents:

- [Deployment](#deployment)
- [Configuration](#configuration)
- [API](#api)
- [Logging](#logging)
- [Tests](#tests)

## Deployment

TBA

## Configuration

Currently the only configuration, necessary is kept [here](./config/default.json)

## Environmental variables

Currently all is set into the config.

## API

The Markdown version of API is available [here](./APIDefinition.md)
The actual Swagger API documentation can be found [here](./src/interface/swagger.json)

## Logging

Logs are sent to standard output by default.

## Tests

Includes unit tests at the moment. Functional and integration are outstanding.

Running the tests:

    npm run test:all

Tests include code coverage via istanbul. See the test/ folder for testing scripts.

### Running Integration Tests interactively

If you want to run integration tests in a repetitive manner, you can startup the test containers using `docker-compose`, login to running `central-settlement` container like so:

```bash
docker-compose -f docker-compose.yml -f docker-compose.integration.yml up

#first time only:
docker exec -it cs_central-ledger sh
npm run migrate

#in a new shell
docker exec -it cs_central-settlement sh
npm run test:int
```

## Auditing Dependencies

We use `npm-audit-resolver` along with `npm audit` to check dependencies for vulnerabilities, and keep track of resolved dependencies with an `audit-resolv.json` file.

To start a new resolution process, run:
```bash
npm run audit:resolve
```

You can then check to see if the CI will pass based on the current dependencies with:
```bash
npm run audit:check
```

And commit the changed `audit-resolv.json` to ensure that CircleCI will build correctly.