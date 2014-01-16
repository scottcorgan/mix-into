# mix-into

Mix objects into other objects

## Install

```
npm isntall mix-into --save
```

## Usage

#### Basic

```js
var mix = require('mix-into');
var baseMixin = {
  baseValue: 'some value',
  baseMethod: function () {
    return baseValue;
  }
};

var obj = {};

mix(baseMixin).into(obj);

obj.baseMethod(); // OUTPUTS: 'some value'
```

#### Partial Function

```js
var mix = require('mix-into');
var baseMixin = mix{
  baseValue: 'some value',
  baseMethod: function () {
    return baseValue;
  }
});
var obj = {};

baseMixin.mixInto(obj);

obj.baseMethod() // OUTPUS: 'some value'
```

#### Nested Mixins

```js
var mix = require('mix-into');
var baseMixin = mix({
  baseValue: 'some value',
  baseMethod: function () {
    return baseValue;
  }
});

var obj = {
  objMethod: function () {
    return this.baseValue;
  }
};
var obj2 = {};

baseMixin.mixInto(obj);
obj.mixInto(obj2); // mixInto method added to each object that's mixed into

obj2.objMethod() // OUTPUS: 'some value'
```

## Run Tests

```
npm install
npm test
```