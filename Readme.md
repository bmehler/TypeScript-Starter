![test workflow](https://github.com/bmehler/TypeScript-Starter/actions/workflows/main.yml/badge.svg?event=push)
# Typescript Starter Project
This is a starter boilerplate template for typescript development. It contains the <strong>vscode debugger configuration</strong> and <strong>testing with jest</strong>. Furthermore the <strong>src folder</strong> is syncronizied with the <strong>out folder</strong> by the <strong>tsc-watch command.</strong>.

## Use it out of the box
```js
git clone https://github.com/bmehler/TypeScript-Starter.git <your_folder>
cd TypeScript-Starter or <your folder>
npm install
npm start
```
This is the tutorial to develop the TypeScript-Starter Boilerplate by your own.
### Create a package.json
```bash
npm init
```
### Load typescript
```bash
npm i typescript --save-dev
```
### Create a tsconfig.json
```bash
npx tsc --init --sourceMap --rootDir src --outDir out
```
### Create a file
```bash
mkdir src
touch index.ts
```
### Prepare VScode for Debugging
```bash
Open Task: Configure Default Build Task
Choose tsc:watch - tsconfig.json

.vscode/tasks.json will be created
```
### Create out folder
```bash
npx tsc
```
### Create files in out folder
```bash
npx tsc --watch

Syncronizing .ts files to .js files in out folder.
```
### Update package.json
```javascript
...
"scripts": {
    "start": "node out/index.js",
    "prestart": "npm run build",
    "build": "tsc",
    "test": "jest",
    "test-coverage": "jest --coverage",
    "tsc-watch": "npx tsc --watch"
  }
...
```
### Create launch.json
```bash
Open Debugging in vscode and click on create launch.json.

Change this line to "type": "node".
```
### If node path not found
Enter <strong>which node</strong> command in Terminal to get the path and add it to <strong>runtimeExecutable</strong> in launch.json.
```bash
{
  ...
  ],
  "runtimeExecutable": "/usr/local/bin/node"
}    
```
### Create a file sum.ts
```typescript
export function sum(a: any, b: any) {
    return a + b;
}
```
### Import sum.ts in index.ts
```typescript
import { sum } from "./sum";

let summe = sum(2,2);

console.log('sum', summe);
```

Set Breakpoints and run the Debugger

## Test your Code with jest

### Install node-packages
```bash
npm i ts-jest --save-dev
npm i --save-dev @types/jest
```

Go to https://kulshekhar.github.io/ts-jest/docs/getting-started/installation/#jest-config-file

### Create a jest.config.js
```bash
npx ts-jest config:init
```
### Put this code into jest.config.js
```typescript
/** @type {import('ts-jest').JestConfigWithTsJest} */
module.exports = {
  "roots": ["src"],
  "transform": { "^.+\\.tsx?$": "ts-jest" }
};
```
### Update files .js files
```bash
npm run tsc-watch
```
### Run Test
```typescript
npm run test

src/sum.test.ts  1 passed
```

### Run Test Coverage
```typescript
npm run test-coverage 1 passed

All files 100%
  sum.ts 100%
```

Have fun!