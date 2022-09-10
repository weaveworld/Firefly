# Firefly Result

## Result 
 
Result files are generated into the result folder.

  - By default, the result is generated into a `@` prefixed and timestamped subfolder of the current folder or into the subfolder given by the `-d` argument 
  - The result folder can be changed using the `-o` argument
  - The output folder contains an `index.html` stub and the `index.firefly.js` that has a one line prefix and all the data in JSON

## Result Data

Result data is written into the `index.firefly.js`, that has an initial line and a JSON. 

  - Result JSON data can be get by skipping the first line; e. g., one can use<br>`tail +2 index.firefly.js`
  - Using [jq](https://stedolan.github.io/jq/), a summary can be get:<br>
    `tail +2 result/index.firefly.js | jq '.|{state,success,warning,error,t}'`

  - main result fields
    - `state` - execution state and result.
      - possible values: `''` (means *'started'*), `'success'`, `'warning'`, `'error'`.
      - `'warning'` and `'error'` states are delegated upward.
    - assertion counter fields:
      - `success` (optional) - number of successful assertions.
      - `warning` (optional) - number of unsuccessful optional assertions.
      - `error` (optional) - number of unsuccessful mandatory assertions.
      - assertion counter fields are summed upward.

    - `t` - execution time  