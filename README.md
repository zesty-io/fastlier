# phastly
functional fastly api with promises

Tested with node4+

Unlike current node libraries, this library seeks to add administrative endpoints such as adding and removing backends, in addition to purging.

In development and does not immediately seek to cover all endpoints but open to it. Pull requests and feature requests welcome.

## Usage


### Promises

```js
import * as fastly from 'phastly'

async function setup(name) {
  fastly.createService(name)
  .then((newService) => {
    // use newService here
  })
}
```

### Async/Await
```js
import * as fastly from 'phastly'

async function setup(name) {
  let newService = await fastly.createService(name)
  // use newService here
}
```
