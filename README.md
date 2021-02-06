# Coding Dojo JS

Coding Dojo for kids to learn JS

## Learn Javascript

W3Schools has this extensive tutorial : https://www.w3schools.com/js/

Also check out JavaScript' [Global Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)

To learn JS on Processing, go [Processing.md](Processing.md)
## Plain Online JS

You can code plain JS on [codesandbox.io](https://codesandbox.io/s/beautiful-river-qv986?file=/src/index.js), which allow you to pratice, save, and share your JS code with the world.

You can also use OpenProcessing
```
function setup() {
	console.log('hello world');
}
```

### CodePen


### React.js

https://www.w3schools.com/react/default.asp


#### React Directly in HTML

Getting started : https://www.w3schools.com/react/react_getstarted.asp

By including 'babel' js library, you can include JSX js file directly without generating the code first.
```
<script src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
<script type="text/babel" src="./script_babel.js"></script>
```
The full working sample looks like this
```
<html>
  <script src="https://unpkg.com/react@16/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
  <body>  
    <div id="mydiv"></div>
    <script type="text/babel">
      class Hello extends React.Component {
        render() { return <h1>Hello World!</h1> }
      }
      ReactDOM.render(<Hello />, document.getElementById('mydiv'))
    </script>
  </body>
</html>
```
### Some libraries
#### d3js.org
#### Dataframe

https://gmousse.gitbooks.io/dataframe-js/content/doc/api/dataframe.html
## APIs

https://devresourc.es/tools-and-utilities/public-apis

### cdnjs.com/libraries

All the JS libraries you can include in your html without installing them first.