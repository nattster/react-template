I followed an instruction on the blog:
[Setting Up Webpack for React and Hot Module Replacement](https://robots.thoughtbot.com/setting-up-webpack-for-react-and-hot-module-replacement)

There are some subtle changes preventing me from using webpack with React.

```
ERROR in ./app.js
Module build failed: SyntaxError: react-template/app/app.js: Unexpected token (5:2)
  3 | 
  4 | React.render(
> 5 |   <Greeting name="World"/>,
    |   ^
  6 |   document.body
  7 | );
```

Here are the steps that I have done to get it to work:

1. `npm init`
2. `npm install webpack -g`
3. `npm install babel-loader babel-core babel-preset-es2015 babel-preset-react --save-dev`
4. `npm install file-loader --save-dev`
5. `npm install react --save`
6. `npm install webpack-dev-server -g`
7. In `webpack.config.js`, I need to change `babel-loader` to

```
{
  test: /\.jsx?$/,
  exclude: /(node_modules|bower_components)/,
  loader: 'babel',
  query: {
    presets: ['react', 'es2015']
  }
}
```


## Build

`webpack --progress --colors`

## Build and rebuild when you made changes

`webpack --progress --colors --watch`

## Dev server

`webpack-dev-server --progress --colors`

Dev server is available at: http://localhost:8080/

I did not try hot module replacement yet.
