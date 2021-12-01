# grunt-contrib-less-fork v1.0.0

# resolve grunt-contrib-lessv3.0.0 eachSeries function complie err

> Compile LESS files to CSS

## Getting Started

If you haven't used [Grunt](https://gruntjs.com/) before, be sure to check out the [Getting Started](https://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](https://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-contrib-less-fork --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-contrib-less-fork');
```

_This plugin was designed to work with Grunt 0.4.x. If you're still using grunt v0.3.x it's strongly recommended that [you upgrade](http://gruntjs.com/upgrading-from-0.3-to-0.4), but in case you can't please use [v0.3.2](https://github.com/gruntjs/grunt-contrib-less-fork/tree/grunt-0.3-stable)._

## Less task

_Run this task with the `grunt less` command._

Task targets, files and options may be specified according to the grunt [Configuring tasks](http://gruntjs.com/configuring-tasks) guide.

### Options

#### paths

Type: `String` `Array` `Function`  
Default: Directory of input file.

Specifies directories to scan for @import directives when parsing. Default value is the directory of the source, which is probably what you want.

If you specify a function the source filepath will be the first argument. You can return either a string or an array of paths to be used.

#### rootpath

Type: `String`  
Default: `""`

A path to add on to the start of every URL resource.

#### compress

Type: `Boolean`  
Default: `false`

Compress output by removing some whitespaces.

#### plugins

Type: `Array`  
Default: `null`

Allows passing plugins.

#### optimization

Type: `Integer`  
Default: `null`

Set the parser's optimization level. The lower the number, the less nodes it will create in the tree. This could matter for debugging, or if you want to access the individual nodes in the tree.

#### strictImports

Type: `Boolean`  
Default: `false`

Force evaluation of imports.

#### strictMath

Type: `Boolean`  
Default: `false`

When enabled, math is required to be in parenthesis.

#### strictUnits

Type: `Boolean`  
Default: `false`

When enabled, less will validate the units used (e.g. 4px/2px = 2, not 2px and 4em/2px throws an error).

#### syncImport

Type: `Boolean`  
Default: `false`

Read @import'ed files synchronously from disk.

#### dumpLineNumbers

Type: `String`  
Default: `false`

Configures -sass-debug-info support.

Accepts following values: `comments`, `mediaquery`, `all`.

#### relativeUrls

Type: `Boolean`  
Default: `false`

Rewrite URLs to be relative. false: do not modify URLs.

#### customFunctions

Type: `Object`  
Default: none

Define custom functions to be available within your LESS stylesheets. The function's name must be lowercase.
In the definition, the first argument is the less object, and subsequent arguments are from the less function call.
Values passed to the function are types defined within less, the return value may be either one of them or primitive.
See the LESS documentation for more information on the available types.

#### sourceMap

Type: `Boolean`  
Default: `false`

Enable source maps.

#### sourceMapFilename

Type: `String`  
Default: none

Write the source map to a separate file with the given filename.

#### sourceMapURL

Type: `String`  
Default: none

Override the default URL that points to the source map from the compiled CSS file.

#### sourceMapBasepath

Type: `String`  
Default: none

Sets the base path for the less file paths in the source map.

#### sourceMapRootpath

Type: `String`  
Default: none

Adds this path onto the less file paths in the source map.

#### sourceMapFileInline

Type: `Boolean`  
Default: `false`

Puts the map (and any less files) as a base64 data uri into the output css file.

#### outputSourceFiles

Type: `Boolean`  
Default: `false`

Puts the less files into the map instead of referencing them.

#### modifyVars

Type: `Object`  
Default: none

Overrides global variables. Equivalent to `--modify-vars='VAR=VALUE'` option in less.

#### banner

Type: `String`  
Default: none

#### process

Type: `Function(content, destinationPath)`
Default: none
Attributes: content, destinationPath

Allows to parse the CSS content to be written to destinationPath to flow through a self defined function.

### Usage Examples

```js
less: {
  development: {
    options: {
      paths: ['assets/css']
    },
    files: {
      'path/to/result.css': 'path/to/source.less'
    }
  },
  production: {
    options: {
      paths: ['assets/css'],
      plugins: [
        new (require('less-plugin-autoprefix'))({browsers: ["last 2 versions"]}),
        new (require('less-plugin-clean-css'))(cleanCssOptions)
      ],
      modifyVars: {
        imgPath: '"http://mycdn.com/path/to/images"',
        bgColor: 'red'
      }
    },
    files: {
      'path/to/result.css': 'path/to/source.less'
    }
  }
}
```
