<h1 align="center">Kn-DB</h1>
<div align="center">

 Data persistence, Based on [Node.js](https://nodejs.org)

Data Storage for Lightweight Node.js Applications

[![npm package](https://img.shields.io/npm/v/kndb.svg?style=flat-square)](https://www.npmjs.org/package/kndb)

</div>

English | [简体中文](./README.CN.md)

## Why use Kn-DB?

- If you need data persistence storage, you don't need to install MySQL/MongoDB anymore.
- Users are no longer required to install other third-party databases when promoting your products.

## Installation

```sh
// with npm
npm install kndb

// with yarn
yarn add kndb
```

## Usage

Here is a quick example to get you started:

```javascript
const knDB = require('kndb');

const db = knDB.getDB('hello');

if (db.success) {
  db.get('knove');       // { a: 0, b: 6 }
  db.set('knove', { a: 7 });
  db.get('knove');       // { a: 7, b: 5 }
} else {
  console.error(db.errorInfo);
}

```

## knDB API
### · getDB(db_name, [option])
Available options:
- type: getDB type, when type = check, if db is undefind, kndb will thorw error, default is create db
   
   s
- position: db saved position, default is your project root position
```javascript
const options = {
    type: 'check',
    position: 'C:\\db', // Linux : 'opt/db/example'
}
const db = knDB.getDB('hello', options);
```
## db API
### · get(table_name)
```javascript
const tableData = db.get('knove'); 
```

### · set(table_name, setData)
```javascript
const setAction = db.set('knove', { a: 7 });
if (setAction.errorInfo) {
    console.error(setAction.errorInfo);
}
```