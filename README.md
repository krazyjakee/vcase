# VCase

The VCase website which facilitates VGo case unboxing and selection for users.

## Overview

This react-redux app uses a [separated client and server, servers, architecture](https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/).

The client aspect is a standalone redux server and all of that is contained within the `client` folder.

The server code exists at root level and may soon be moved to a `server` folder.

## Development

You will need Node.js >= 8.9.4 `nvm install 8.9.4`

Install dependencies

```
$ make build
```

Launch the backend API server and the front end client server in one shot.

```
$ STEAM_API_KEY="STEAM API KEY" make dev
```

Also run the VGo mock server for a simple local development flow.

```
$ make vgo-mock
```

## Production

You will need Node.js >= 8.9.4 `nvm install 8.9.4`

Install dependencies

```
$ make build
```

Generate static files

```
$ make static-files
```

Run the server

```
$ NODE_ENV=production STEAM_API_KEY="STEAM API KEY" BASE_URL="http://vcase.gg" SESSION_KEY="SOME_RANDOM_KEY" PORT=3000 VGO_URL="https://api-trade.opskins.com" VGO_API_KEY="SOME_API_KEY" AFFILIATE_ADDRESS="0x939826f5acff002bf6b898fb8151cac83b2401" npm run server
```

### Configuration variables

* NODE_ENV: It allows the usage of default values for development and QA environments. It needs to be set to 'production' for any other environment including staging.
* STEAM_API_KEY: This is the key used for login integration with steam. It can be generated here https://steamcommunity.com/dev/apikey
* BASE_URL: The URL where this website is available (will be used to construct redirect URLs from external services)
* SESSION_KEY: Random base64 key used for signing and verifying the cookie used to store session data. A secure key can be generated by running: *openssl rand -base64 32*
* PORT: The port where the application will listen for HTTP requests
* VGO_URL: URL of the WAX ExpressTrade API.
* VGO_API_KEY: VCase API key generated from [IUser/CreateVCaseUser](https://github.com/OPSkins/trade-opskins-api/blob/master/IUser/CreateVCaseUser.md)
* AFFILIATE_ADDRESS: Ethereum address of the account to be used for collecting payments for openings generated from this site.

## Monitoring

The application provides a simple health check endpoint that can be used to monitor the status of the app.

```
$ curl http://localhost:3000/health
{"api":"up"}
```

Given that this project has no external dependencies other than the VGO API the health of the nodejs server itself is the only thing that needs to be monitored.

The server logs to the standard output by default.

## Tutorials

* https://medium.com/@notrab/getting-started-with-create-react-app-redux-react-router-redux-thunk-d6a19259f71f
* https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/
* https://github.com/facebook/create-react-app
* https://www.sohamkamani.com/blog/2016/06/05/redux-apis/
