# React Notes
Here I keep my notes about React JS.

### Working with global variables from other libraries
Some libraries require you to include their CDN then use their global variables. 
[Here](https://stackoverflow.com/questions/43714895/google-is-not-defined-in-react-app-using-create-react-app) explains how you should use it. 
```
const google = window.google;
// then you can use google
```

