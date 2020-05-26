#### Detect language with IP address (langip)

✔️ **Free** & Easy

✔️ Clean & **Fast**

✔️ Zero dependency & **No limit**

✔️ **Without** need licence key

✔️ No **HTTP** connection

✔️ **Ip2Location** database

✔️ Includeds **Arabic**, **Persian**, **Chinese**, **Spanish**, **French**, **Turkish**, **Korean** as default

---

#### Usage

-   Install

```bash
npm install langip --save
```

-   As multi language detector

```javascript
const langip = require("langip")


/* async await */
async () => {
    let lang = await langip.detect("8.8.8.8","En")  /* detect(ip,fallback) */
    console.log(lang)   /* En */
})


/* promise */
langip.detect("103.127.119.132").then((lang) => {
    console.log(lang)   /* Fa */
})
```

-   As specific language **(recommended)**
-   Arabic **(Ar)**

```javascript
/*
    Arabic [Ar]
    Countries [SA, IQ, KW, BH, AE, QA, OM]
*/

const isAr = require("langip/language/Ar")

/* async await */
async () => {
    let status = await isAr("194.31.220.14")    /* isAr(ip) */
    console.log(status) /* true */
})

/* promise */
isAr("1.1.1.1").then((status) => {
    console.log(status) /* false */
})
```

-   Persian **(Fa)**

```javascript
/*
    Persian [Fa]
    Countries [IR, AF, TJ]
*/

const isFa = require("langip/language/Fa")

/* async await */
async () => {
    let status = await isFa("8.8.8.8")  /* isFa(ip) */
    console.log(status) /* false */
})

/* promise */
isFa("103.127.119.132").then((status) => {
    console.log(status) /* true */
})
```

-   Chinese **(Zh)**

```javascript
/*
    Chinese [Zh]
    Countries [CN, SG, TW]
*/

const isZh = require("langip/language/Zh")

/* async await */
async () => {
    let status = await isZh("8.8.8.8")  /* isZh(ip) */
    console.log(status) /* false */
})

/* promise */
isZh("103.70.53.52").then((status) => {
    console.log(status) /* true */
})
```

-   Spanish **(Es)**

```javascript
/*
    Spanish [Es]
    Countries [ES, MX]
*/

const isEs = require("langip/language/Es")

/* async await */
async () => {
    let status = await isEs("8.8.8.8")  /* isEs(ip) */
    console.log(status) /* false */
})

/* promise */
isEs("192.148.167.205").then((status) => {
    console.log(status) /* true */
})
```

-   French **(Fr)**

```javascript
/*
    French [Fr]
    Countries [FR, CD]
*/

const isFr = require("langip/language/Fr")

/* async await */
async () => {
    let status = await isFr("8.8.8.8")  /* isFr(ip) */
    console.log(status) /* false */
})

/* promise */
isFr("188.115.112.51").then((status) => {
    console.log(status) /* true */
})
```

-   Turkish **(Tr)**

```javascript
/*
    Turkish [Tr]
    Countries [TR]
*/

const isTr = require("langip/language/Tr")

/* async await */
async () => {
    let status = await isTr("8.8.8.8")  /* isTr(ip) */
    console.log(status) /* false */
})

/* promise */
isTr("217.195.200.161").then((status) => {
    console.log(status) /* true */
})
```

-   Korean **(Ko)**

```javascript
/*
    Korean [Ko]
    Countries [KR]
*/

const isKo = require("langip/language/Ko")

/* async await */
async () => {
    let status = await isKo("8.8.8.8")  /* isKo(ip) */
    console.log(status) /* false */
})

/* promise */
isKo("134.75.232.150").then((status) => {
    console.log(status) /* true */
})
```

---

#### Utility

```javascript
const { utility } = require("langip")

/* ipTolong(ip) */
let long = utility.ipTolong("2.16.158.255")
console.log(long) /* 34643711 */

/* longToip(long) */
let ip = utility.longToip(42991616)
console.log(ip) /* 2.144.0.0 */
```

---

#### Build

For update IP2Location database or add new language detector

-   Downloading latest database

```bash
npm run download
```

-   config convert in _**build/config.json**_

    -   ISO [639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php) Language Code List
    -   List of [official](https://en.wikipedia.org/wiki/List_of_languages_by_the_number_of_countries_in_which_they_are_recognized_as_an_official_language#List) languages

```json
{
    "languages": {
        "Ar": ["SA", "IQ", "KW", "BH", "AE", "QA", "OM", "EG", "SD"],
        "Fa": ["IR", "AF", "TJ"],
        "Zh": ["CN", "SG", "TW"],
        "Es": ["ES", "MX"],
        "Fr": ["FR", "CD"],
        "Tr": ["TR"],
        "Ko": ["KR"]
    }
}
```

-   Converting large database file to small chunk files

```bash
npm run convert
```

---

#### Test

```bash
npm run test
```

-   Detect

```bash
 PASS  test/detect.test.js
  √ detect [195.16.171.140] => [Ar] (16 ms)
  √ detect [109.122.208.134] => [Fa] (4 ms)
  √ detect [103.70.53.52] => [Zh] (2 ms)
  √ detect [192.148.167.205] => [Es] (3 ms)
  √ detect [188.115.112.51] => [Fr] (3 ms)
  √ detect [217.195.200.161] => [Tr] (2 ms)
  √ detect [134.75.232.150] => [Ko] (2 ms)
  √ detect [0.0.0.0] => [fallback] (1 ms)
```

-   isAr

```bash
 PASS  test/isAr.test.js
  √ isAr [185.217.8.116] => [true] (3 ms)
  √ isAr [0.0.0.0] => [false]
```

-   isFa

```bash
 PASS  test/isFa.test.js
  √ isFa [185.78.234.76] => [true] (4 ms)
  √ isFa [0.0.0.0] => [false] (1 ms)
```

-   isZh

```bash
 PASS  test/isZh.test.js
  √ isZh [113.17.217.136] => [true] (16 ms)
  √ isZh [0.0.0.0] => [false] (1 ms)
```

-   isEs

```bash
 PASS  test/isEs.test.js
  √ isEs [216.251.66.182] => [true] (7 ms)
  √ isEs [0.0.0.0] => [false] (1 ms)
```

-   isFr

```bash
 PASS  test/isFr.test.js
  √ isFr [5.144.136.101] => [true] (9 ms)
  √ isFr [0.0.0.0] => [false] (2 ms)
```

-   isTr

```bash
 PASS  test/isTr.test.js
  √ isTr [185.160.114.220] => [true] (4 ms)
  √ isTr [0.0.0.0] => [false] (6 ms)
```

-   isKo

```bash
 PASS  test/isKo.test.js
  √ isKo [103.19.124.87] => [true] (9 ms)
  √ isKo [0.0.0.0] => [false] (1 ms)
```

-   Utility

```bash
 PASS  test/utility.test.js
  √ utility [Ar] [34643456] => [2.16.158.0] (2 ms)
  √ utility [Ar] [2.16.158.255] => [34643711]
  √ utility [Fa] [42991616] => [2.144.0.0]
  √ utility [Fa] [2.147.255.255] => [43253759]
  √ utility [Zh] [16777472] => [1.0.1.0]
  √ utility [Zh] [1.0.3.255] => [16778239]
  √ utility [Es] [34605056] => [2.16.8.0]
  √ utility [Es] [2.16.8.255] => [34605311] (1 ms)
  √ utility [Fr] [33554432] => [2.0.0.0]
  √ utility [Fr] [2.15.255.255] => [34603007] (17 ms)
  √ utility [Tr] [34625536] => [2.16.88.0]
  √ utility [Tr] [2.16.88.255] => [34625791] (1 ms)
  √ utility [Ko] [17498112] => [1.11.0.0]
  √ utility [Ko] [1.11.255.255] => [17563647]
```

---

#### IP2Location

This package includes [IP2Location](https://lite.ip2location.com) LITE data
