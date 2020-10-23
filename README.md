MathType for CKEditor 5 [![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/wirismath)
===

Type and handwrite mathematical notation with MathType.

Easily include quality math equations in your documents and digital content.

![MathType for CKEditor 5 screenshot](http://www.wiris.com/portal/themes/wiris_com/img/others/ckeditor_plugin_npm.png)

# Table of Contents

- [Install instructions](#install-instructions)
- [Services](#services)
- [Documentation](#documentation)
- [Displaying on Target Page](#displaying-on-target-page)

## Install instructions

1. Install the npm module:

   ```
   npm install @wiris/mathtype-ckeditor5
   ```

2. Update the CKEditor configuration by adding the new plugin and including the MathType and ChemType buttons:

   ```js
   import MathType from '@wiris/mathtype-ckeditor5/src/plugin';

   ...

   ClassicEditor
        .create( editorElement, {
            plugins: [ ..., MathType, ... ],
            toolbar: {
                items: [
                    ...
                    'MathType',
                    'ChemType',
                    ...
                ]
            },
   ```

## Services

This npm module uses remotely hosted services to render MathML data. In case of wanting to install these services on your own backend, please contact <support@wiris.com>.

[comment]: <> (TODO: fill this section when the documentation is ready)

## Displaying on Target Page

In order to display mathematical formulas on the target page, i.e. the page where content produced by the HTML editor will be visible, the target page needs to include the [MathType script](https://docs.wiris.com/en/mathtype/mathtype_web/integrations/mathml-mode#add_a_script_to_head). For example for the default setting this would be:
```html
<script src="https://wiris.net/demo/plugins/app/WIRISplugins.js?viewer=image"></script>
```
To load data into the vue you should use the following method:
```js
WirisPlugin.Parser.initParse(htmlData);
```
For instance, the following call:
```js
WirisPlugin.Parser.initParse('<math><mo>x</mo></math');
```
Returns the following image:
```html
<img style="max-width: none; vertical-align: -4px;" class="Wirisformula" src="data:image/svg+xml;charset=utf8,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20xmlns%3Awrs%3D%22http%3A%2F%2Fwww.wiris.com%2Fxml%2Fcvs-extension%22%20height%3D%2219%22%20width%3D%2213%22%20wrs%3Abaseline%3D%2215%22%3E%3C!--MathML%3A%20%3Cmath%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F1998%2FMath%2FMathML%22%3E%3Cmo%3Ex%3C%2Fmo%3E%3C%2Fmath%3E--%3E%3Cdefs%3E%3Cstyle%20type%3D%22text%2Fcss%22%2F%3E%3C%2Fdefs%3E%3Ctext%20font-family%3D%22Arial%22%20font-size%3D%2216%22%20text-anchor%3D%22middle%22%20x%3D%226.5%22%20y%3D%2215%22%3Ex%3C%2Ftext%3E%3C%2Fsvg%3E" data-mathml="Â«mathÂ»Â«moÂ»xÂ«/moÂ»Â«/mathÂ»" alt="x" role="math" width="13" height="19" align="middle"/>
```

If you add the following JavaScript code into the previous example:
```js
var htmlElement = document.getElementById('example');
var data = 'Initial data: <math><msqrt><mo>x</mo></msqrt></math>'
htmlElement.innerHTML = WirisPlugin.Parser.initParse(data);
```
The HTML data will be inserted into the edit area by replacing the MatML with its correspondent image.

## Documentation

To find out more information about MathType, please go to the following documentation:

[comment]: <> (TODO: link to install instructions)
* [MathType documentation](http://docs.wiris.com/en/mathtype/mathtype_web/start)
* [Introductory tutorials](http://docs.wiris.com/en/mathtype/mathtype_web/intro_tutorials)
* [Service customization](http://docs.wiris.com/en/mathtype/mathtype_web/integrations/config-table)
* [Testing](http://docs.wiris.com/en/mathtype/mathtype_web/integrations/html/plugins-test)
