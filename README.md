# Text Editor Application

![License Badge](https://img.shields.io/badge/License-MIT-blue)  
[Deployed Application](https://editmytext.herokuapp.com/)  
[GitHub Repository](https://github.com/atmason90/text-editor)

## Table of Contents

- [Description](#description)
- [Screenshot](#screenshot)
- [Code Examples](#code-examples)
- [Core Technologies Used](#core-technologies-used)
- [Questions](#questions)
- [License](#license)

## Description

The purpose of this project was to build a single-page text editor application that runs in the browser and is also installable as a PWA (Progressive Web Application). This application uses an IndexedDB database to get and store data. specifically, methods from the `idb` package were used to implement data persistence.

## Screenshot

![Screen Shot 2022-05-25 at 9 13 44 PM](https://user-images.githubusercontent.com/99947655/170415655-04e1212d-d1d4-4145-ba93-cc7bebc7e5b3.png)

## Code Examples

This example displays the use of the `idb` package methods to store data on the IndexedDB database.

```js
export const putDb = async (id, content) => {
  console.log("PUT request to the database");
  const jateDb = await openDB("jate", 1);
  const tx = jateDb.transaction("jate", "readwrite");
  const store = tx.objectStore("jate");
  const request = store.put({ id: id, content: content });
  const result = await request;
  console.log("data saved to the database", result);
};
```

This example displays how asset caching was implemented in the code.

```js
registerRoute(
  ({ request }) => ["style", "script", "worker"].includes(request.destination),
  new StaleWhileRevalidate({
    cacheName: "asset-cache",
    plugins: [
      new CacheableResponsePlugin({
        statuses: [0, 200],
      }),
    ],
  })
);
```

## Core Technologies Used

![JavaScript Badge](https://img.shields.io/badge/Language-JavaScript-yellow)
![CSS Badge](https://img.shields.io/badge/Language-CSS-blue)
![Node.js Badge](https://img.shields.io/badge/Environment-Node.js-green)
![IndexedDB Badge](https://img.shields.io/badge/Database-IndexedDB-informational)
![idb Badge](https://img.shields.io/badge/NPM-idb-red)
![Express Badge](https://img.shields.io/badge/NPM-Express.js-yellowgreen)
![heroku Badge](https://img.shields.io/badge/Deployment-heroku-blueviolet)

## Questions

If you have any questions regarding this project, please reach out to me via email at [atmason90@gmail.com](mailto:atmason90@gmail.com).

You can view my other projects on GitHub by visiting my [profile](https://github.com/atmason90).

## License

MIT License

Copyright (c) 2022 Andrew Mason

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
