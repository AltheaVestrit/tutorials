# Blog Project - Notes
Following along with [Make a blog with Node.js, Express and MongoDB](https://www.youtube.com/playlist?list=PL4cUxeGkcC9hAJ-ARcYq_z6lDZV7kT1xD).

## EJS Layouts
### Packages
NPM depencies:
* ejs
* express-ejs-layouts

### Set up EJS Layouts
`/app.js`
```js
// Import EJS Layouts
const expressLayout = require('express-ejs-layouts');

// Define Templating Engine
app.use(expressLayout);
app.set('layout', './layouts/main'); // Set custom default layout to /views/layouts/main.ejs
app.set('view engine', 'ejs'); // Set view engine to EJS
```
By default, Express sets the default views folder to `<project root>/views`, so it's not necessary to explicitly define this folder.

### Define default Layout
`/views/layouts/main.ejs`
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

    <%- body %> <!-- This is where the View content is inserted -->

</body>

</html>
```

### Define a View
The Express-EJS-Layouts package will take this view and use the default layout (defined above) to render the page.
`/views/index.ejs`
```html
<h1>Home</h1>
```

### Render View using default Layout
Render `/views/index.ejs` view using `/views/layouts/main.ejs` as layout.

`/server/routes/mainRouter.js`
```js
router.get('', (req, res) => {
    res.render('index'); // Renders view: /views/index.ejs
});
```