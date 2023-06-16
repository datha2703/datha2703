1. Bookmarks
   1. https://www.testim.io/blog/mocha-for-typescript-testing/
1. Install node and npm from https://nodejs.org/en/download/. Single  installer brings both Node and NPM

1. `npm -v;node -v;` - Check version number

2. `sudo npm cache clear --force` - clear cache 

1. Start projects by executing below commands
`npm init -y`
`tsc --init `

1. Mocha is test runner
`sudo npm install mocha -g`
`mocha --version`

1. TS Node is Precompiler to run TS script from mocha
`sudo npm install ts-node -g`
`ts-node -v`
`mocha --require ts-node/register ./scripts/*.ts`

1. Install and uninstall dependencies globally. Globally libraries are stored in /usr/local/lib/node_modules.
`npm install -g sinon @types/sinon`
`npm list -g` - shows list installed libs
`npm sinon --version -g`
`npm uninstall -g sinon @types/sinon`
`npm install -g chai @types/chai --save-dev` - Installs two libraries chai and @types/chai

1. Install and uninstall dependencies locally. Local libraries are stored in ./node_modules.
`npm install -g sinon @types/sinon`
`npm list` - List locally installed libraries
`npm uninstall -g sinon @types/sinon`
`npm install chai @types/chai --save-dev` - Installs two libraries chai and @types/chai

1. npm install | how it works https://www.stackchief.com/tutorials/npm%20install%20%7C%20how%20it%20works
`npm install`
npm install downloads a package and it's dependencies
npm install can be run with or without arguments.
When run without arguments, npm install downloads dependencies defined in a package.json file and generates a node_modules folder with the installed modules.
