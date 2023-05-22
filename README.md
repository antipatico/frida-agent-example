## frida-agent-example
This fork allows for easy usage of [frida-tsplugin](https://github.com/antipatico/frida-tsplugin).
### How to compile & load

```sh
$ git clone git://github.com/oleavr/frida-agent-example.git
$ cd frida-agent-example/
$ npm install
$ frida -U -f com.example.android --no-pause -l _agent.js
```

### Development workflow

To continuously recompile on change, keep this running in a terminal:

```sh
$ npm run watch
```

And use an editor like Visual Studio Code for code completion and instant
type-checking feedback.

### Installing frida-tsplugin
1. clone [frida-tsplugin](https://github.com/antipatico/frida-tsplugin) it in a local directory
2. align the typescript version in this repo `package.json` and in your [frida-tsplugin](https://github.com/antipatico/frida-tsplugin)
3. point your [frida-tsplugin](https://github.com/antipatico/frida-tsplugin) dependency in your `package.json` to your local path.
4. in VS Code
    1. open this project
    2. open a typescript file
    3. press `CTRL+P` and search for `TypeScript: Select TypeScript version...`
    4. select `Use Workspace version`

So for example in [package.json](./package.json) you have:
```json
{
  "dependencies": {
    "typescript": "^5.0.4",
    "frida-tsplugin": "file:~/src/frida-tsplugin"
  }
}
```

**NB!** the `typescript` version  must be the same for your [frida-tsplugin](https://github.com/antipatico/frida-tsplugin)'s `package.json`.

Everytime you change typescript version, **run in your [frida-tsplugin](https://github.com/antipatico/frida-tsplugin) folder:**

```sh
npm run compile
```

And rerun in this project folder:
```sh
npm install
```

Then be sure to run the [frida-tsplugin](https://github.com/antipatico/frida-tsplugin)'s agent with
```sh
frida -U -l agent/tsplugin.js -f com.example.target
```
**After that**, with the agent up and running, open VS Code.
