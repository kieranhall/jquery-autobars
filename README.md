jQuery Autobars
================

A convenient jquery plugin for loading handlebars templates declared in script tags!


Usage
================

jQuery-autobars's sweet spot is cases where you want to have your
handlebars templates in their own file/files.

This plugin makes the distinction between partials files (which
can hold multiple handlebars templates) and full templates which are one
per file.

You can load a handlebar template to load into $.handlebarTemplates["compiled template"]
with the script tag.

```html
	<script src="/main.hbs" type="text/x-handlebars-template"></script>
```
Autobars looks at the src and downloads the code as needed, compiles it into
a handlebars template and adds the method to the $.handlebarTemplates space where you can use it in your projects!!


A partials file contains several handlebar template source files and are between
```html
	<!--#?index-->
	  handlebars code goes here
	<!--#?end-->
```
Handlebars helper knows its a a partials file via a script tag with type

```html
	<script src="/helper-templates.hbs" type="text/handlebar-partials"></script>
```
in this case the type="text/handlebar-partials" marks the file for additional parsing.

The name after the ? in the top indicates the name the template will have in
the partials namespace and can be accessed at the handlebarTemplates namespace
under jquery.
```javascript
	$(document).autoBars(function() {
		/* you pass a callback in to perform work on the templates
		becasuse handlebar helper is making multiple aynchrous requests
		and it makes sure to not call this callback till all the necessary files
		are loaded into the $.handlebarsTemplates namespace.
		*/
        console.log('it worked!!')
        var $html = $.handlebarTemplates.partials.index({
            message: "hello welcome to handlebar helper!!",
        });
        $('body').append($html);
      });
```


