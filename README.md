# Blogging App

This is a comprehensive blogging application with full CRUD (Create, Read, Update, Delete) functionalities. Users can sign up, sign in, add blogs, and comment on blogs. The application uses MongoDB for the database, JWT tokens for authentication, and EJS for server-side rendering.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Running the Application](#running-the-application)
- [Project Structure](#project-structure)
- [Routes](#routes)
- [Middleware](#middleware)
- [Models](#models)

## Features

- User Authentication (Sign Up, Sign In)
- Create, Read, Update, Delete (CRUD) functionalities for blogs
- Comment on blogs
- JWT-based authentication
- EJS for server-side rendering
- Secure password storage using hashing and salting

## Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT (JSON Web Tokens)
- EJS (Embedded JavaScript templating)
- dotenv
- Cookie-parser
- Crypto

## Prerequisites

Ensure you have the following installed on your local development machine:

- Node.js (>=14.x.x)
- npm (>=6.x.x)
- MongoDB

## Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/yourusername/blogging-app.git
   cd blogging-app
   ```

2. Install the dependencies:
   ```sh
   npm install
   ```

## Environment Variables

Create a `.env` file in the root directory and add the following variables:

```plaintext
PORT=8000
MONGO_URL=your_mongo_connection_string
```

Replace `your_mongo_connection_string` with your actual MongoDB connection string.

## Running the Application

1. Start the MongoDB server if it's not already running:

   ```sh
   mongod
   ```

2. Start the application:

   ```sh
   npm start
   ```

3. Open your browser and navigate to:
   ```sh
   http://localhost:8000
   ```

## Project Structure

```plaintext
.
├── controllers
│   ├── user.js
│   ├── blog.js
├── middlewares
│   ├── authentication.js
├── models
│   ├── user.model.js
│   ├── blog.model.js
├── routes
│   ├── user.js
│   ├── blog.js
├── views
│   ├── home.ejs
│   ├── login.ejs
│   ├── register.ejs
│   ├── blog.ejs
├── public
│   ├── css
│   ├── js
├── .env
├── .gitignore
├── package.json
├── server.js
```

## Routes

- `/user`

  - `GET /register` - Render registration page
  - `POST /register` - Handle user registration
  - `GET /login` - Render login page
  - `POST /login` - Handle user login
  - `GET /logout` - Handle user logout

- `/blog`
  - `GET /` - Get all blogs
  - `GET /:id` - Get blog by ID
  - `POST /` - Create a new blog
  - `PUT /:id` - Update blog by ID
  - `DELETE /:id` - Delete blog by ID

## Middleware

- `checkForAuthenticationCookie` - Middleware to check for JWT authentication cookie

## Models

- **User**

  - `fullName`: String, required
  - `email`: String, required, unique
  - `salt`: String
  - `password`: String, required
  - `profileImageUrl`: String, default `/images/default.png`
  - `role`: String, enum `["USER", "ADMIN"]`, default `USER`

- **Blog**
  - `title`: String, required
  - `body`: String, required
  - `coverImageUrl`: String
  - `createdBy`: ObjectId, ref `user`, required

## Additional Information

For any issues or feature requests, please open an issue on the [GitHub repository](https://github.com/yourusername/blogging-app/issues).
