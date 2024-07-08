# Authentication

The repository contains:

- Distributed code from **eCentennial** used to build a server for **Authentication**.
- `/.devcontainer`: Configuration file used by **Codespaces** to determine operating system.
- `/.vscode`: Configuration file used by **Codespaces** to configure Visual Studio Code settings.
- `/client/.eslintrc`: Settings for [ESLint](https://eslint.org/) included for code consistency and quality.
- `/client/.prettierrc`: Settings for [Prettier](https://prettier.io/) used to format code.
- `package.json` and `yarn.lock`: Defines the application information for [Node.js](https://nodejs.org/), dependent packages, and the versions needed for each.

### Getting Started

Select **Open in GitHub Codespaces** and then **Create codespace**. **GitHub** will prepare the development environment with all the necessary dependencies already installed.

### Update .env File

Reference the example provided `.env.example` to create `.env`.

```.env
MONGODB_URI=mongodb+srv://your_user:your_password@your_cluster.mongodb.net/YourDatabase?retryWrites=true&w=majority&appName=YourApp/yourcollection
```

### Start the Server

After setting up the environment variables, start the server.

```sh
yarn start
```

## Test the REST API

1. **Open Thunder Client:**

   - Open **Thunder Client** readily installed in **Codespaces** by clicking on its icon on the sidebar.

2. **Create a New Request:**

   - In **Thunder Client**, click on the **New Request** button to start setting up the API request.
   - Enter the API endpoint URL in the URL field: `http://localhost:3000/api/users`.
   - Select the HTTP method `POST` from the dropdown next to the URL field.

3. **Set Up Request Body:**

   - Click on the "Body" tab, choose the content type, and enter the JSON data.

4. **Send the Request:**

   - Click the "Send" button to execute the request. **Thunder Client** will display the response from the API, including status code, response time, and the body.

5. **Review the Response:**
   - On **MongoDB Cloud**, click on the **Database** section then **Browse Collections**.

## Example Endpoints

### Get all users

- **URL:** `http://localhost:3000/api/users`
- **Method:** `GET`
- **Response:**

  ```json
  [
    {
      "_id": "6685a5c88475a1bf8c42586b",
      "name": "New User",
      "email": "newuser@example.com",
      "created": "2024-07-03T19:26:00.891Z",
      "updated": "2024-07-03T19:26:00.891Z"
    }
  ]
  ```

### Resgister a new user

- **URL:** `http://localhost:3000/api/users`
- **Method:** `POST`
- **Body:**

  ```json
  {
    "name": "New User",
    "username": "newuser",
    "email": "newuser@example.com",
    "password": "password123"
  }
  ```

- **Response:**

  ```json
  {
    "message": "Successfully signed up!"
  }
  ```

### Log a user in

- **URL:** `http://localhost:3000/auth/signin`
- **Method:** `POST`
- **Body:**

  ```json
  {
    "email": "newuser@example.com",
    "password": "password123"
  }
  ```

- **Response:**

  ```json
  {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2Njg1YTVjODg0NzVhMWJmOGM0MjU4NmIiLCJpYXQiOjE3MjAwMzUyOTN9.oUT4Tn16PBaoM2nmko0CePyLpi3E1TnOFxYODi8K-R0",
    "user": {
      "_id": "6685a5c88475a1bf8c42586b",
      "name": "New User",
      "email": "newuser@example.com"
    }
  }
  ```

### Fetch a user

- **URL:** `http://localhost:3000/api/users/668c033d124f409871ef99b8`
- **Method:** `GET`
- **Headers:**
  ```
  Accept: */*
  User-Agent: Thunder Client (https://www.thunderclient.com)
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJfaWQiOiI2NjhjMDMzZDEyNGY0MDk4NzFlZjk5YjgiLCJpYXQiOjE3MjA0NTIyNzR9.4o_NbVH2pzQoaXsyylhMbmFoJeP70IG3MkDN8IY5YzI
  Accept: */*
  Accept-Encoding: gzip, deflate, br
  Connection: keep-alive
  ```
- **Response:**
  ```json
  {
      "_id": "668c033d124f409871ef99b8",
      "name": "New User",
      "email": "newuser@example.com",
      "created": "2024-07-08T15:18:21.846Z",
      "updated": "2024-07-08T15:18:21.846Z",
      "__v": 0
  }
  ```


### Log a user out

- **URL:** `http://localhost:3000/auth/signin`
- **Method:** `GET`
- **Response:**

  ```json
  {
    "message": "signed out"
  }
  ```