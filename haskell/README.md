# Haskell Example

This example is based on react-flux.

## Building

### For the first time

1. cd haskell
1. npm install

### Each time

1. stack build
1. make

## Running the App with Webpack's "watch mode":

1. If the (dev) dependencies in package.json were changed: npm install
1. npm start
1. Wait until `webpack: bundle is now VALID.` appears
1. Point your browser at http://localhost:9090

The browser window will be refreshed whenever the local JavaScript changes.

## Creating Static Assets to be delivered by the Server

1. If the (dev) dependencies in package.json were changed: npm install
1. npm run build
1. Deliver `js-build/` from the backend.
