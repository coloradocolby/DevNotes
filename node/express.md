# Node and Express


#### Middleware

Middleware is function that gets called before everything loads. The location middleware is specified is **VERY** important. Take the following code snippet for example. If  ```index.html``` is inside the ```/build```, then the middleware function ```app.use()``` will find it and the ```app.get()``` will never be executed.

```
app.use(express.static(path.resolve(__dirname, 'build')))


app.get('/', (req, res) => {
  res.sendFile(path.resolve(__dirname, 'build', 'index.html'));

});

```

If the static files happen to be in ```build/static```, then the middleware should look like the following:

```
app.use('/static', express.static(path.resolve(__dirname, 'build', 'static')))
```

Express tells Node to look in ```build/static``` and make those files accessible in the ```example.com/static``` path.

### Another example:

Given the following file structure: `public -> static -> js, img, css` If you write

`app.use(express.static(path.resolve(__dirname, 'public', 'static')));`

static files will be available directly in root `coloradocolby.co/js/particles.json`

**HOWEVER** If you write
`app.use('/static', express.static.....)`

static files will be available in static folder `coloradocolby.co/static/js/particles.json`
