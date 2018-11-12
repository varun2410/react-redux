# used React + Redux w/ ES6 Starter Project

## Getting Started
npm install
make a copy of .env.dist.js with name .env.js and edit variable accordingly

## Development

Steps to install ***node*** and ***npm***
* `$ sudo apt-get install curl python-software-properties`
* `$ sudo curl -sL https://deb.nodesource.com/setup_10.13.x | sudo -E bash -`
* `$ sudo apt-get install nodejs`
* `$ hash -r`

* Install all the packages using npm:
  * `$ npm install`

* Hot reloading via webpack middlewares:
  * `$ npm start`
  * Point your browser to http://localhost:3000/, page hot reloads automatically when there are changes

## Testing

**(TBD)**

To execute all unit tests, use:

```sh
$ npm run test
```

To run unit tests continuously during development (watch tests), use:

```sh
$ npm run test:watch
```

## Expose App on Your Local Dev Machine

Assign yourself a unique publicly accessible url that will proxy all requests to your locally running webserver.

```sh
$ npm install -g localtunnel
$ npm start
$ npm run tunnel # run in a new tab
```

You will receive a url, for example `https://tbst.localtunnel.me`, that you can share with anyone for as long as your local instance of `lt` remains active. Any requests will be routed to your local service at the specified port.

## Error Tracking and Insights with Sentry

In order to get info on errors that happened in production, we integrate [Sentry](https://sentry.io/for/javascript/) into our application to track errors and get context on what happened.

To use it on your side, configure it first:

* Create account at [https://sentry.io/signup/](https://sentry.io/signup/)
* Add new project for your app on Sentry website
* In `/src/client/assets/javascripts/app/config.js` file assign `SENTRY_KEY` and `SENTRY_APP` constants values that you got after adding a new project
* Don't forget to define `Allowed Domains` section under your `Project Settings` on Sentry website to track errors from required domains

## Debugging

For debugging purposes please use:
- [Redux DevTools
](https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd) plugin for Chrome to simplify debugging React apps.
- [React Developer Tools](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

## FAQ

### What's this for?

This starter kit implements best practices like testing (`unit testing`), minification, bundling, and so on. It saves you from the long, painful process of wiring it all together into an automated dev environment and build process.

### What's happening under the hood when I run `npm start`?

Webpack serves your app in memory when you run `npm start`. No physical files are written. However, the web root is `/src`, so you can reference files under /src in index.html. When the app is built using `npm run build`, physical files are written to `/build` folder and the app is served from `/build`.

### How is Sass being processed?

We're handling it differently in DEV vs PROD.

When you run `npm start`:

 1. The sass-loader compiles Sass into CSS
 2. Webpack bundles the compiled CSS into app.js. Sounds weird, but it works!
 3. app.js contains code that loads styles into the &lt;head&gt; section of index.html via JavaScript. This is why there is no stylesheet reference in index.html. In fact, if you disable JavaScript in your browser, you'll see the styles don't load either.

The approach above supports hot reloading, which is great for development. However, it also create a flash of unstyled content on load because you have to wait for the JavaScript to parse and load styles before they're applied. So for the production build, we use a different approach:

When you run `npm run build`:

 1. The sass-loader compiles Sass into CSS
 2. The [extract-text-webpack-plugin](https://github.com/webpack/extract-text-webpack-plugin) extracts the compiled Sass into app.css
 3. buildHtml.js adds a reference to the stylesheet to the head of index.html.

### How do I deploy this?

`npm run build`. This will prepare and build the project for production use. It does the following:

- Minifies all JS and CSS
- Inline base64 URLs for images and fonts if their size is less than specified limit
- Sets NODE_ENV to `production` so that React is built in production mode
- Places the resulting built project files into `/build` directory. (This is the folder you'll expose to the world).

## License

[MIT License](https://nicksp.mit-license.org/), 2016

Brought to you by Nick S. Plekhanov