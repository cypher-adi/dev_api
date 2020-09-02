# Dev APIs

Backend API for dev_api application to manage bootcamps, courses, reviews, users and authentication.

Ensure adding config.env inside the config folder in the root directory with the following data.

```
NODE_ENV = <environment_name>
PORT = <port_no>
MONGO_URI = <mongodb__connection_string>
GEOCODER_PROVIDER= mapquest
GEOCODER_API_KEY=<api_key>
FILE_UPLOAD_PATH= ./public/uploads
MAX_FILE_UPLOAD=1048576
JWT_SECRET=<secret_key>
JWT_EXPIRE=30d
```

> - For Geocoder provider you may use Mapquest, OpenCage, Google Premier
> - FILE_UPLOAD_PATH defines the folder to upload the image.
> - Maximum image file upload size is set to **1048576 bytes** (**1 MB**).
> - Add a secret key to sign the jwt tokens.
> - JWT_EXPIRE sets the expiry time for the token.

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
