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
JWT_COOKIE_EXPIRE=30

SMTP_HOST=<host>
SMTP_PORT=<port>
SMTP_EMAIL=<email>
SMTP_PASSWORD=<password>
FROM_EMAIL=noreply@<domain_name>
FROM_NAME=<Name>
```

> - For Geocoder provider you may use Mapquest, OpenCage, Google Premier
> - FILE_UPLOAD_PATH defines the folder to upload the image.
> - Maximum image file upload size is set to **1048576 bytes** (**1 MB**).
> - Add a secret key to sign the jwt tokens.
> - JWT_EXPIRE sets the expiry time for the token.
> - JWT_COOKIE_EXPIRE sets the expiry time for the cookie.
> - For nodemailer **SMTP** email setup use your email configurations like gmail, outlook, etc.

---

<br>

> To install all the necessary dependencies

```bash
npm install
```

> To start the server in development mode

```bash
npm run dev
```

> To start the server in production mode

```bash
npm start
```

---

## ◄ _Route Functionalities_ ►

### Bootcamps

- List all bootcamps in the database
  - Pagination
  - Select specific fields in result
  - Limit number of results
  - Filter by fields
- Search bootcamps by radius from zipcode
  - Use a geocoder to get exact location and coords from a single address field
- Get single bootcamp
- Create new bootcamp
  - Authenticated users only
  - Must have the role "publisher" or "admin"
  - Only one bootcamp per publisher (admins can create more)
  - Field validation via Mongoose
- Upload a photo for bootcamp
  - Owner only
  - Photo will be uploaded to local filesystem
- Update bootcamps
  - Owner only
  - Validation on update
- Delete Bootcamp
  - Owner only
- Calculating the average cost of all courses for a bootcamp
- Calculating the average rating from the reviews for a bootcamp

### Courses

- List all courses for bootcamp
- List all courses in general
  - Pagination, filtering, etc
- Get single course
- Create new course
  - Authenticated users only
  - Must have the role "publisher" or "admin"
  - Only the owner or an admin can create a course for a bootcamp
  - Publishers can create multiple courses
- Update course
  - Owner only
- Delete course
  - Owner only

### Reviews

- List all reviews for a bootcamp
- List all reviews in general
  - Pagination, filtering, etc
- Get a single review
- Create a review
  - Authenticated users only
  - Must have the role "user" or "admin" (no publishers)
- Update review
  - Owner only
- Delete review
  - Owner only

### Users & Authentication

- Authentication using JWT/cookies
  - JWT and cookie expires in 30 days
- User registration
  - Register as a "user" or "publisher"
  - Once registered, a token is sent along with a cookie (token = xxx)
  - Passwords are hashed
- User login
  - User can login with email and password
  - Plain text password gets compared with stored hashed password
  - Once logged in, a token is sent along with a cookie (token = xxx)
- User logout
  - Cookie is sent to set token = none
- Get user
  - Route to get the currently logged in user (via token)
- Password reset (lost password)
  - User can request to reset password
  - A hashed token is emailed to the users registered email address
  - A put request can be made to the generated url to reset password
  - The token expires after 10 minutes
- Update user info
  - Authenticated user only
  - Separate route to update password
- User CRUD
  - Admin only
- Users can only be made admin by updating the database field manually

## Security

- Encrypt passwords and reset tokens
- Prevent NoSQL injections
- Add headers for security (helmet)
- Prevent cross site scripting - XSS
- Add a rate limit for requests of 100 requests per 10 minutes
- Protect against http param polution
- Use cors to make API public

For complete Documentation with examples, [Click Here](https://documenter.getpostman.com/view/10834035/TVCiSRLk).

#### Author

> Aditya Kumar [Cypher](https://github.com/cypher-adi)
