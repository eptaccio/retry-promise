# await-retry

# install
`npm i await-retry --save`

# usage example
```js
const { retry } = require('await-retry')

function getUser () {
  return {
    message: 'wow, amazing',
    user: {
      name: 'enzo'
    }
  }
}

function getUserWithError () {
  throw new Error('oh no')
}

async function start () {
  console.log(await retry(getUser, { tries: 2 }))
  /**
    {
     tries: 1,
     success: true,
     result: { message: 'wow, amazing', user: { name: 'enzo' } },
    }
   */

  console.log(await retry(getUserWithError, { tries: 2 }))
  /**
   * {
       tries: 2,
       success: false,
       errors: [Error: oh no..., Error: oh no]
     }
   */
}

start()
```
