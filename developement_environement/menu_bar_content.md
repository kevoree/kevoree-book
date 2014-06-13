# Menu bar content

#### File menu
 Menu item      | Description                                                                                                              | Shortcut
--------------- | ------------------------------------------------------------------------------------------------------------------------ | ---------------
Load            | Load a model from a JSON file client-side                                                                                | Ctrl+L
Merge           | Same as "Load" but merging given model with the current model in KWE                                                     | Ctrl+M
Open from node  | Load a model from a remote node reachable using [Kevoree WebSocket protocol](developement_environement/known_protocols.md)| Ctrl+O
Merge from node | Same as "Open from node" but merging retrieved model with the current model in KWE                                       | Ctrl+Shift+M
Save as JSON    | Save the current model in KWE to a JSON file client-side                                                                 | Ctrl+S

#### Model menu
 Menu item                 | Description                                                                                       | Shortcut
-------------------------- | ------------------------------------------------------------------------------------------------- | ---------
Clear All                  | Reset the current model to an empty one (empty TypeDefinition list and empty model graph)         | Alt+A
Clear Instances            | Delete every instances in the current model (empty model graph)                                   | Alt+I
Clear Unused Type Defs     | Parse the current model in order to remove the unused TypeDefinition (no instance means unused)   | Alt+U
Kevoree Standard Libraries | Open the **Kevoree Standard Libraries** popup ([see](developement_environement/kwe_popups.md#kevoree-standard-libraries)) | Alt+K
From custom repository     | Open the **From custom repository** popup ([see](developement_environement/kwe_popups.md#from-custom-repository))         | <none>
Custom push                | Open the **Custom push** popup ([see](developement_environement/kwe_popups.md#custom-push))                               | <none>

#### Edit menu
 Menu item      | Description                                                                 | Shortcut
--------------- | --------------------------------------------------------------------------- | ---------
Undo            | Undo last model modification (:exclamation: **NOT IMPLEMENTED YET**)        | Ctrl+Z
Redo            | Redo last model modification (:exclamation: **NOT IMPLEMENTED YET**)        | Ctrl+Y
Settings        | Configure your KWE settings (saved locally using your browser LocalStorage) | Ctrl+K
Server settings | Open the **Server settings** popup ([see](developement_environement/kwe_popups.md#server-settings)) | Ctrl+H

#### KevScript menu
Open the **KevScript** popup ([see below](#kevscript))

#### Help menu
Open the **Help** popup ([see below](#help))