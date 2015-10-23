# Generalities

## Naming rules
> The following rules have not been followed by the past. Don't be surprise to find some unconventional names from time to time. They will be kept that way for legacy.
The java platform in particular follow its own naming rules.

> The following rules are also in a draft state. Feel free to contact the Kecoree Core Team if you found them hazy.

 1. Every Kevoree related component should be prefixed with "kevoree" (e.g. [kevoree-book](https://github.com/kevoree/kevoree-book), [kevoree-browser-runtime](https://github.com/kevoree/kevoree-browser-runtime), [kevoree-web-editor](https://github.com/kevoree/kevoree-web-editor))
 2. Every component related to a specific platform should be prefixed with "kevoree-${platform}" (e.g. [kevoree-js](https://github.com/kevoree/kevoree-js), [kevoree-dotnet](https://github.com/kevoree/kevoree-dotnet)).
 3. Every generic component (i.e. described in the [platform itegration](README.md) part of the book) have a common name who should be followed platforms wide (e.g. [kevoree-js-kevscript](https://github.com/kevoree/kevoree-js-kevscript), [kevoree-donet-annotation](https://github.com/kevoree/kevoree-dotnet-annotation)). The following list is a uncomprehensive list of reserved keywords.
   * kevscript
   * core
   * runtime
   * model
   * annotation
 4. Every deployable component name should follow the form "kevoree-${platform}-${componentType}-${typeDefName}" where **componentType** is *node*, *group*, *chan* or *comp* (Respectivelly for the Node, Group, Channel and Component). The **typeDefName** should be consistent among the various implementations of the same type definition (e.g. [kevoree-dotnet-group-remotews](https://github.com/kevoree/kevoree-dotnet-group-remotews), [kevoree-js-comp-ticker](https://github.com/kevoree/kevoree-js-comp-ticker)).
