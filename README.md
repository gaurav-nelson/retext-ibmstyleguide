# retext-ibmstyleguide
Word usage guidence for technical writers.

`retext-ibmstyleguide` is a [retext](https://github.com/wooorm/retext) plugin for the word usage advice in [IBM style guide](https://www.redbooks.ibm.com/Redbooks.nsf/ibmpressisbn/9780132101301?Open).  It highlights errors and provide word usage advice.

## Installation

[npm](https://docs.npmjs.com/cli/install):

```bash
npm install retext-ibmstyleguide
```

## Usage

For the following file, `example.txt`:

```text
You can utilize a shorter word.
Be advised, don’t do this.
That’s the appropriate thing to do.
```

And our script, `example.js`, looks as follows:

```javascript
var vfile = require('to-vfile');
var report = require('vfile-reporter');
var retext = require('retext');
var ibmstyleguide = require('retext-ibmstyleguide');

retext()
  .use(ibmstyleguide)
  .process(vfile.readSync('example.txt'), function (err, file) {
    console.error(report(err || file));
  });
```

Yields:
```text
   1:9-1:16  warning  utilize [v.] Replace with "use."               utilize  ibmstyleguide
  2:19-2:21  warning  do (a step) [v.] Use "complete" or "perform."  do       ibmstyleguide
  3:33-3:35  warning  do (a step) [v.] Use "complete" or "perform."  do       ibmstyleguide

⚠ 3 warnings

```

## API

### `retext().use(ibmstyleguide)`

## Rules
See [index.json](https://github.com/gaurav-nelson/retext-ibmstyleguide/blob/master/index.json)
