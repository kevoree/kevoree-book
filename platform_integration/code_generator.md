# Code generator
The Kevoree Registry is a public application, accessible at http://registry.kevoree.org.  
This application is basically a map of TypeDefinition <-> DeployUnit links. It is used to resolve
the components, nodes, channels and groups binaries based on their TypeDefinition.  

With that in mind, when adding a new platform to the Kevoree eco-system, it might be convenient to
provide a code generator that is able to scaffold projects for the new targeted platform language.  

The idea behind that is to ease the creation of a new DeployUnit for a specific TypeDefinition.
Because the registry knows all about the available TypeDefinitions, and because a TypeDefinition
contains all the necessary information to create a code skeleton (type, dictionary attributes, inputs, outputs).
One could create a library that takes developer inputs to determine a TypeDefinition name and version, and then
create the code skeleton for that specific TypeDefinition using the targeted language paradigm.

## Example
In JavaScript, the code generator is provided by the Yeoman [generator-kevoree](https://github.com/kevoree/generator-kevoree).
This generator is a command-line Node.js application that prompts questions to
the developer in order to, in the end, create a **kevoree-js** project.

```sh
$ yo kevoree

Kevoree Project Generator:

[?] Would you like to start from an existing TypeDefinition from the Kevoree Registry? Yes
[?] Specify a TypeDefinition fully qualified name (eg. Ticker or my.company.MyType) org.kevoree.library.Ticker
[?] Which version would you like to use? (40 total versions) 5.2.10
[?] Choose your NPM module name: kevoree-comp-ticker
[?] Do you want this to be runnable by the browser runtime? No
[?] What is the license of your module? (MIT) LGPL-3.0

# ... keep on answering
```

And finally, the generator will create a clean project based on the Kevoree Registry TypeDefinition named **Ticker** in version **5.2.10** in the example:

```
$ tree -L 2
.
├── browser
│   ├── kevoree-comp-ticker.html
│   └── ui-config.json
├── Gruntfile.js
├── kevs
│   └── main.kevs
├── lib
│   └── Ticker.js
├── node_modules
│   ├── grunt
│   ├── grunt-browserify
│   ├── grunt-contrib-uglify
│   ├── grunt-contrib-watch
│   ├── grunt-kevoree
│   ├── grunt-kevoree-genmodel
│   ├── grunt-kevoree-registry
│   └── kevoree-entities
├── package.json
└── README.md
```

With the **Ticker** skeleton be:

```js
var AbstractComponent = require('kevoree-entities').AbstractComponent;

var Ticker = AbstractComponent.extend({
    toString: 'Ticker',

    dic_random: {
        optional: true,
        defaultValue: false,
    },
    dic_period: {
        optional: true,
        defaultValue: 3000,
    },

    start: function (done) {
        this.log.debug(this.toString(), 'START');
        done();
    },

    stop: function (done) {
        this.log.debug(this.toString(), 'STOP');
        done();
    },

    out_tick: function (msg) { /* noop */ },

    uiController: function () {
        return [function () {
            // ui controller
        }];
    }
});

module.exports = Ticker;
```
