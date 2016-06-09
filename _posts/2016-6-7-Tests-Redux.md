---
layout: post
title: Unit Tests in Redux
---

Unit testing is an automated method of testing individual units of code to assure they are fit for use. The main goal of unit testing is to separate each part of your software and show that all parts are correct.

# Configuration

To run our Redux tests, we must define a testing framework and an assertion library. We'll use [Mocha](http://mochajs.org/) and [Expect](https://www.npmjs.com/package/expect).

To install both of them:

`npm install --save-dev mocha`

`npm install --save expect`

Since we are going to write of all our code in ES6, so we must use [Babel](http://babeljs.io/) as a transpiler.

`npm install --save-dev babel-register`

```bash
// .babelrc
{
  "presets": ["es2015"]
}
```

We must also add a couple of lines to `scripts` in the `package.json` file:

```bash
{
  ...
  "scripts": {
    ...
    "test": "mocha --compilers js:babel-register --recursive",
  },
  ...
}
```

And to run all of ours tests, we use `npm test`.

# Testing Action

In Redux, actions are payload of information that send data from your application to your store. They are functions which return plain objects.

## Example

We have an action that takes a show name and it will return an object with the argument we passed to it in its payload property.

```javascript
import * as types from '../constants';

export const selectShow = (show) => ({
    type: types.SELECTED_SHOW,
    payload: show
})
```

So to test this action, we must simply pass an argument to it and expect that the returned object will contain the argument in its payload property.

```javascript
import expect from 'expect';
import * as types from '../../src/constants';
import * as actions from '../../src/actions/index';

describe('actions', () => {
  it('should create an action to select a show', () => {
    const show = 'Lost';
    const expectedAction = {
      type: types.SELECTED_SHOW,
      payload: show
    };

    expect(actions.selectShow(show)).toEqual(expectedAction);
  });
})
```

## Testing Reducers

In Redux, a reducer receives an action and returns a new state based on the current state and action.

## Example

```javascript
import * as types from '../constants';

export default function(state = null, action) {
  switch (action.type) {
    case types.SELECTED_SHOW:
      return action.payload;
  }
  return state;
}
```

So to test this reducer, we expect that the state returned from it will be the payload property of action.

```javascript
import expect from 'expect'
import reducer from '../../src/reducers/reducer_selected_show';
import * as types from '../../src/constants'

describe('selected show reducer', () => {
  it('should handle SELECTED_SHOW', () => {
    const show = 'Lost';

    expect(reducer([], {
      type: types.SELECTED_SHOW,
      payload: show
    })).toEqual(show);
  });
})
```
