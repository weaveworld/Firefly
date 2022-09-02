# Firefly Result

## Result 
 
Result files are generated into the result folder.

  - By default, the result is generated into a `@` prefixed and timestamped subfolder of the current folder
  - The result folder can be changed using the `-o` argument
  - The output folder contains an `index.html` stub and the `index.firefly.js` that has a one line prefix and all the data in JSON

## Result Data

  - result JSON data can be get by skipping the first line
    - e. g., one can use<br>`tail -n +2 index.firefly.js`

  - main result fields
    - `state` - execution state and result.
      - possible values: `''` (means 'started'), `'success'`, `'error'`, `'failure'`.
      - `'error'` and `'failure'` states are delegated upward.
    - assertion fields:
      - `success` (optional) - number of successful assertions.
      - `error` (optional) - number of erroneous assertions.
      - `failure` (optional) - number of failed assertions.
      - assertion fields are summed upward.

    - `$t` - execution time  