A template for modules
======
#### from https://github.com/mmikowski/spa

> Include purpose author, and copyright info in the header
```Javascript
/* Module_template.js
 *
 */
```
### Namespace and Module Scope Variable
> Create namespace for the module using a **self-executing function**.
> This prevents accidental creation of global JavaScript variables.
> Only one namespace schild be defined per file, 
> and the file name should correlate precisely
> For example if module provide the **spa.shell** 
> namespace file name should be **spa.shell.js**
```Javascript
spa.module = (function () {
//-- BEGIN MODULE SCOPE VARIABLE 
var
  configMap = {
    settable_map : { bool_color : true },
    color_name : 'blue'
  },
  stateMap = { $container : null},
  jqueryMap = {},
  
  setJqueryMap, configModule, initModule;
//-- END MODULE SCOPE VARIABLE 
```
> Declare and initialize modules-scope variables
> we commonly include **configMap** to store module configuration,
> **stateMap** to store run-time state values, and 
> **jqueryMap** to cache jQuery collections

### Private Utility
> These private methods dont manipulate DOM and therefore don't require browser
> *If method has utilty betond a single module*,
> *we should move it to a shared library such as spa.util.js*
```JavaScript
//-- BEGIN UTILITY METHODS
  copyAnchorMap = function () {
    return $.extend( true, {}, stateMap.anchor_map );
  };
//-- END UTILITY METHODS
```
### DOM Methods
> These private methods access and modify the DOM and therefore
> require browser to run
> An Example DOM method might move a CSS sprite.
> *The setJqueryMap method should be used to to cache jQuery collection*

```JavaScript
//-- BEGIN DOM METHOD
setJqueryMap = function () {
  var $container = stateMap.$container;
  
  jqueryMap = { $container : $container };
};
//-- END DOM METHOD
```
### Private Event Handler
> These methods  handle events such as a button click, a key press, a browser window resize
> or receipt of a wev socket message. Event handlers should generally call 
> DOM methods to adjust the DOM instead of making changes themselves
```Javascript
onClickButton = ...
```

### Callbacks
> Group all callback methods in their own section. They're quasi public methods
> since they're used by external modules to which they have been provided

### Public Methods
> These methods are part of a module's pubic interface. This section should include
> The **configModule** and **initModule** methods if they're provided
```Javascript
configModule = function ( input_map ) {
  spa.util.setConfigMap({
    input_map     : input_map,
    settable_map  : configMap.settable_map,
    config_map    : configMap
  });
  return true;
};

initModule = function ( $container ) {
  stateMap.$container = $container;
  setJqueryMap();
  return true;
}
```

### return 
> Neatly return the public methods in an object
```Javascript
return {
  configModule : configModule,
  initModule : initModule
  };
```

