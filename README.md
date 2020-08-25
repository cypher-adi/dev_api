# Dev APIs

Backend API for dev_api application to manage bootcamps, courses, reviews, users and authentication.

Ensure adding config.env inside the config folder in the root directory with the following data.

```
NODE_ENV = <environment_name>
PORT = <port_no>
MONGO_URI = <mongodb__connection_string>
GEOCODER_PROVIDER= mapquest
GEOCODER_API_KEY=<api_key>
```

> For Geocoder provider you may use Mapquest, OpenCage, Google Premier

---

<br>

> To start the server in development mode

```bash
npm run dev
```

> To start the server in production mode

```bash
npm start
```

#### Author

> Aditya Kumar [Cypher](https://github.com/cypher-adi)
