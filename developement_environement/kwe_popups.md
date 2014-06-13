# KWE popups
#### Server settings
Because KWE is a standalone Web application, it gives you the possibility to specify the server you want to connect to.
To specify your own KWE-server, use this popup.
By default, [editor.kevoree.org](http://editor.kevoree.org) uses an **Express** web server hosted on the same machine.
 > You can clone the sources of [kevoree/kevoree-web-editor-server](https://github.com/kevoree/kevoree-web-editor-server) and deploy it on your own servers

![KWE Server settings](http://hosta.braindead.fr/raw/539980c11a9879c239a1a21e)

#### Kevoree Standard Libraries
This popup allows you to merge Kevoree's official TypeDefinitions to your current model.
Kevoree Standard Libraries are available (currently, June 2014) for 3 platforms:
 - Java
 - Javascript
 - Cloud

Once the list loaded, you can select wanted libraries and hit the **Merge libraries** button and wait for the server you are connected to (specified in the popup title after @), to answer your request with the according Kevoree model.

![KWE Std Libs](http://hosta.braindead.fr/raw/539980bd1a9879c239a1a21d)

#### From custom repository
If you want to merge your own Kevoree libraries from a custom Maven repository you can by using this popup.
This will trigger the resolving server-side, then it will retrieve the model of your library (still server-side) and send it back to KWE, resulting in a merge of your current KWE model and the one you have specified in this popup.

![KWE Custom repo](http://hosta.braindead.fr/raw/539980cc1a9879c239a1a221)

#### Custom push
Sometimes you have to edit your model network attributes resulting in the impossibility for you to push your model to your platforms (your group WebSocket server won't be able to receive the model according to the new network attributes, because it is still launched on the old model network attributes)
Using this popup, you can specify a group WebSocket server directly and ask for a push of your current model by pressing **Push model**

![KWE Custom push](http://hosta.braindead.fr/raw/539980cf1a9879c239a1a222)

#### KevScript
A [Kevoree Script](http://kevoree.org/doc/#kevoree-script-aka-kevscript) (aka KevScript) editor providing syntax highlighting and auto-completion.
By default, this KevScript editor content is dinamically created according to the current model (model2kevs processing), but you can also change the content by using the provided examples (dropdown selector in the top-right corner).
Once you are done editing, you have two choices:
 - **Download**: saves the current KevScript to a **.kevs** file client-side
 - **Run**: process your script and updates the current Kevoree model in KWE

![KWE KevScript](http://hosta.braindead.fr/raw/539993c91a9879c239a1a223)

The KevScript Editor also provides some shortcuts to improve user experience:

 Action       |    Shortcut
------------- | --------------
Search        | Ctrl+F
Find next     | Ctrl+G
Find previous | Ctrl+Shift+G
Replace       | Ctrl+Shift+F
Replace all   | Ctrl+Shift+R


#### Help
This popup contains the whole list of shortcuts available in KWE, plus some useful information concerning the editor.

![KWE Help](http://hosta.braindead.fr/raw/539980c91a9879c239a1a220)
