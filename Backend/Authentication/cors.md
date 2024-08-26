
[Cors](https://www.npmjs.com/package/cors) PH-61_3 00:00

```js
const cors = require('cors');
app.use(
  cors({
    origin: ["http://localhost:5173",
      "http://localhost:5174",
      "http://localhost:5175",
      "http://localhost:5176",
    ],
    credentials: true,
  })
);
```