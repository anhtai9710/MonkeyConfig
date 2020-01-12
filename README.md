MonkeyConfig
============

MonkeyConfig is a simple configuration library for user scripts. It allows for
easy creation of configuration dialog windows and takes care of storing and
retrieving the configuration parameters for the script.

Usage Example
-------------

Tell your user script to use MonkeyConfig by placing a `@require` directive in
the metadata section:

```javascript
// ==UserScript==
// @name           AwesomeScript
// @require        https://raw.github.com/odyniec/MonkeyConfig/master/monkeyconfig.js
```

Then, call `MonkeyConfig()` to construct your configuration object:

```javascript
var cfg = new MonkeyConfig({
    title: 'AwesomeScript Configuration',
    menuCommand: true,
    params: {
        font_size: {
            type: 'select',
            choices: [ 'Small', 'Medium', 'Large' ],
            default: 'Medium'
        },
        auto_adjust: {
            type: 'checkbox',
            default: true
        }
    }
});
```

And that's pretty much it. MonkeyConfig builds a configuration dialog based on
the passed data. It also adds a menu item in the User Script Commands menu to open the
configuration dialog.

At any time in your script, you can retrieve the value of a configuration
parameter with the `get()` method:

```javascript
var auto_adjust = cfg.get('auto_adjust');
```

and set a new value using the `set()` method:

```javascript
cfg.set('font_size', 'Small');
```

Supported Data Types
--------------------

* checkbox
* number
* select
* text
* color
    * default value must be a hex color value