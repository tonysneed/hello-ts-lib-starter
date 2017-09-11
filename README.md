# Hello TypeScript Library Starter

[![Build Status](https://travis-ci.org/tonysneed/hello-ts-lib-starter.svg?branch=master)](https://travis-ci.org/tonysneed/hello-ts-lib-starter)
[![Coverage Status](https://coveralls.io/repos/github/tonysneed/hello-ts-lib-starter/badge.svg?branch=master)](https://coveralls.io/github/tonysneed/hello-ts-lib-starter?branch=master)
[![Greenkeeper badge](https://badges.greenkeeper.io/tonysneed/hello-ts-lib-starter.svg)](https://greenkeeper.io/)

A sample project for TypeScript Library Starter.

Docs published to: <https://tonysneed.github.io/hello-ts-lib-starter>

### Source

Using: **typescript-library-starter**
- GitHub Repo: <https://github.com/alexjoverm/typescript-library-starter>.
- Blog post: <https://dev.to/alexjoverm/write-a-library-using-typescript-library-starter>

### Customization

- Linting:
  + Copy tslint.json from angular project.
  + Install packages.

  ```
  npm i --save-dev codelyzer @angular/compiler@^2.3.1 @angular/core@^2.3.1 zone.js@^0.7.2
  ```

  + Remove Prettier (conflicts with TSLint) by 
    removing *precommit*, *lint-staged* from package.json
  + Update *lint* script in package.json to include --type-check.

  ```json
  "lint": "tslint --type-check -p tsconfig.json codeFrame 'src/**/*.ts' 'test/**/*.ts'"
  ```


- Exports:
  + Add ts file with same name as project
  + Add exports for modules

  ```js
  export { HelloWorld } from './hello-world';
  export { ItalianHelloWorld } from './italian-hello-world';
  ```

- TypeScript:
  + Update to latest version: `npm i --save-dev typescript`
  + Target es2015 in tsconfig.json.
  + Update suffix in *module* in package.json to es2015

- Update **.gitignore** from an Angular project.
  + Remove *.vscode* entry

- Debugging:
  + Add **launch.json** to **.vscode* folder for debugging Jest tests.

  ```json
  {
    "version": "0.2.0",
    "configurations": [
      {
        "name": "Tests",
        "type": "node",
        "request": "launch",
        "program": "${workspaceRoot}/node_modules/jest/bin/jest.js",
        "sourceMaps": true,
        "runtimeArgs": [
          "-i"
        ],
        "env": {
          "NODE_ENV": "development"
        },
        "outFiles": [
          "${workspaceRoot}/dist/**/*"
        ],
        "cwd": "${workspaceRoot}"
      }
    ]
  }
  ```

- Tasks:
  + Add **tasks.json** to **.vscode** folder for binding to keyboard shortcuts for 
  *build*, *test* and *lint* tasks.

  ```json
  {
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "npm",
            "script": "build",
            "presentation": {
                "reveal": "always"
            },
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": [
                "$tsc"
            ]
        },
        {
            "label": "test",
            "type": "npm",
            "script": "test:watch",
            "presentation": {
                "reveal": "always"
            },
            "group": {
                "kind": "test",
                "isDefault": true
            }
        },
        {
            "taskName": "lint",
            "type": "shell",
            "command": "npm run lint",
            "problemMatcher": [
                "$tsc"
            ]
        }
    ]
  }
  ```

### Automation

- Open repo in [GitHub Desktop](https://desktop.github.com) and publish repo to GitHub.
  + Open in GitHub, copy the clone url.
  + Paste into the *url* property of *repository* in package.json.

- Link repo to [Travis CI](https://travis-ci.org) account.
 + Copy markdown for *Build Status* badge into README.md.

- Link repo to [Coveralls](https://coveralls.io) account.
  + Copy markdown for *Coverage Status* into README.md.

- Link repo to [Greenkeeper](https://greenkeeper.io) account.
  + Merge PR created by the Greenkeeper bot.
  + Add markdown for *Greenkeeper* badge to README.md.

- Enable automated releases.
  + Prepare hooks

  ```
  npm run semantic-release-prepare
  ```

  + Install and run [semantic release](https://github.com/semantic-release/semantic-release).
  + Answer "no" when promoted to generate .travis.yml.

  ```
  npm install -g semantic-release-cli
  semantic-release-cli setup
  ```

 ### Docs

- Push or merge PR to master to publish docs.
  + Docs for this repo published to: <https://tonysneed.github.io/hello-ts-lib-starter>

- To locate generated docs, open repo on GitHub
  + Go to Settings for the repo, GitHub Pages section
  + Uses TypeDoc: http://typedoc.org

- Configure project to exclude tests from docs.
  + Update build script to add: `--exclude '**/*.spec.ts'`

- Use JavaDoc tags to document classes, methods, etc.
  + See http://typedoc.org/guides/doccomments/
  + Use jsdoc comments extension for VS Code: https://marketplace.visualstudio.com/items?itemName=stevencl.addDocComments
  + Example:

  ```js
  /**
  * Class representing a greeter.
  */
  export class HelloWorld {
    /**
    * Greet someone by name.
    * @param  {string} name
    * @returns A friendly greeting.
    */
    greet(name: string): string {
      return `Hello ${name}`;
    }
  }
  ```

