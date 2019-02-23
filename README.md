# countries-list-cat

This is a fork project countries-list-cat created by Andreas Wittig

A project with Catalonia as a Country with Iso CT and CAT.

i18n for ISO 3166-1 country codes. We support Alpha-2, Alpha-3 and Numeric codes from http://en.wikipedia.org/wiki/ISO_3166-1#Officially_assigned_code_elements

## Installing

Install it using npm: `npm install countries-list-cat`

This library requires that [String#padStart](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart) is available. If your environment does not support this method, you will need to [polyfill](https://www.npmjs.com/package/core-js) it.

If used in a browser environment, you will need to manually install the local you wish to support.

```javascript
var countries = require("countries-list-cat");

// Support french & english languages.
countries.registerLocale(require("countries-list-cat/langs/en.json"));
countries.registerLocale(require("countries-list-cat/langs/fr.json"));
```

## Code to Country

### Get the name of a country by it's ISO 3166-1 Alpha-2, Alpha-3 or Numeric code

`````javascript
var countries = require("countries-list-cat");
console.log("US (Alpha-2) => " + countries.getName("US", "en")); // United States of America
console.log("US (Alpha-2) => " + countries.getName("US", "de")); // Vereinigte Staaten von Amerika
console.log("USA (Alpha-3) => " + countries.getName("USA", "en")); // United States of America
console.log("USA (Numeric) => " + countries.getName("840", "en")); // United States of America
`````

### Get all names by their ISO 3166-1 Alpha-2 code

`````javascript
var countries = require("countries-list-cat");
console.log(countries.getNames("en")); // { 'AF': 'Afghanistan', 'AL': 'Albania', [...], 'ZM': 'Zambia', 'ZW': 'Zimbabwe' }
`````

### Supported languages (ISO 639-1)

* `ca`: Catalan
* `da`: Danish
* `de`: German
* `en`: English
* `es`: Spanish
* `fr`: French
* `it`: Italian
* `ja`: Japanese
* `ko`: Korean
* `pl`: Polish
* `pt`: Portuguese
* `ru`: Russian
* `zh`: Chinese
* `eu`: Euskera


[List of ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)

### Country to Code

`````javascript
var countries = require("countries-list-cat");
console.log("United States of America => " + countries.getAlpha2Code('United States of America', 'en'));
// United States of America => US

console.log("United States of America => " + countries.getAlpha3Code('United States of America', 'en'));
// United States of America => USA
`````

## Codes

### Convert Alpha-3 to Alpha-2 code

`````javascript
var countries = require("countries-list-cat");
console.log("USA (Alpha-3) => " + countries.alpha3ToAlpha2("USA") + " (Alpha-2)");
// USA (Alpha-3) => US (Alpha-2)
`````

### Convert Numeric to Alpha-2 code

`````javascript
var countries = require("countries-list-cat");
console.log("840 (Numeric) => " + countries.numericToAlpha2("840") + " (Alpha-2)");
// 840 (Numeric) => US (Alpha-2)
`````

### Convert Alpha-2 to Alpha-3 coe
`````javascript
var countries = require("countries-list-cat");
console.log("DE (Alpha-2) => " + countries.alpha2ToAlpha3("DE") + " (Alpha-3)");
// DE (Alpha-2) => DEU (Alpha-3)
`````

### Convert Numeric to Alpha-3 code

`````javascript
var countries = require("countries-list-cat");
console.log("840 (Numeric) => " + countries.numericToAlpha3("840") + " (Alpha-3)");
// 840 (Numeric) => USA (Alpha-3)
`````

### Convert Alpha-3 to Numeric code

`````javascript
var countries = require("countries-list-cat");
console.log(countries.alpha3ToNumeric("SWE"));
// 752
`````

### Convert Alpha-2 to Numeric code

`````javascript
var countries = require("countries-list-cat");
console.log(countries.alpha2ToNumeric("SE"));
// 752
`````

### Get all Alpha-2 codes

`````javascript
var countries = require("countries-list-cat");
console.log(countries.getAlpha2Codes());
// { 'AF': 'AFG', 'AX': 'ALA', [...], 'ZM': 'ZMB', 'ZW': 'ZWE' }
`````

### Get all Alpha-3 codes

`````javascript
var countries = require("countries-list-cat");
console.log(countries.getAlpha3Codes());
// { 'AFG': 'AF', 'ALA': 'AX', [...], 'ZMB': 'ZM', 'ZWE': 'ZW' }
`````

### Get all Numeric codes

`````javascript
var countries = require("countries-list-cat");
console.log(countries.getNumericCodes());
// { '004': 'AF', '008': 'AL', [...], '887': 'YE', '894': 'ZM' }
`````

## Contribution

To add a language:

* add a json file under langs/
* add the language to the `data` object in enty-node.js at the top
* add language to section **Supported languages** in README.md
* add language to keywords in package.json
* run `npm install && make test` to make sure that tests are passing
* open a PR on GitHub
