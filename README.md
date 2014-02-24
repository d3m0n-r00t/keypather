#value-for-keypath [![Build Status](https://travis-ci.org/tjmehta/value-for-keypath.png?branch=master)](https://travis-ci.org/tjmehta/value-for-keypath)
##Get a value from an object using a keypath string. Supports bracket notation, dot notation, and functions

###installation
```bash
npm install value-for-keypath
```

###usage
####mixed notation:
```js
var valueForKeypath = require('value-for-keypath');
var obj = {
  foo: function () {
    return {
      bar: {
        baz: 'val'
      }
    };
  }
};
valueForKeypath(obj, "foo()['bar'].baz"); // val
```

####dot notation:
```js
var valueForKeypath = require('value-for-keypath');
var obj = {
  foo: {
    bar: {
      baz: 'val'
    }
  }
};
valueForKeypath(obj, "foo.bar.baz"); // val
```

####bracket notation:
```js
var valueForKeypath = require('value-for-keypath');
var obj = {
  foo: {
    bar: {
      baz: 'val'
    }
  }
};
valueForKeypath(obj, "['foo']['bar']['baz']"); // val
```

####functions:
```js
var valueForKeypath = require('value-for-keypath');
var obj = {
  foo: function () {
    return function () {
      return function () {
        return 'val';
      };
    };
  }
};
valueForKeypath(obj, "foo()()()"); // val
```
