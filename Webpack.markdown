## webpack
Four core modules.
### webpack.config.js
#### dependency
web app在处于生产状态时用到的modules. EX: React, jQuery.
#### devDependency
web app在处于开发状态时要用到的modules. EX: webpack. web-server.
### Entry
The entry point is where webpack will start the bundling. webpack will find corresponding module
recursively.
### Output
For outputting the bundled JS file, we need to specify the file path (absolute path), file name.  
### Loader
webpack can only bundle and analyze JS code. For Other file type, we need loader. What loader does
is enable webpack load and analyze non-JS file. We config loader in module.rules.
#### Babel
一系列module。Convert ES6 JS code to ES5 version
##### Babelrc
Babel的配置文件
#### SASS converter
如SASS转化为CSS的那个module
#### Pollyfill
For some browser, we have to convert features in ES6 such as Promise or some methods
like Array.from() to ES5.
### Plugin
Add more functions to webpack. We config plugins in the 'plugins' array of module.export.
### Next.js和普通打包的区别
普通的webpack打包是把整个JS打包在一起，Next.js是把各个component的JS都分开打包好了
### Enhance front-end performance by webpack
Please read the Performance file.  
 