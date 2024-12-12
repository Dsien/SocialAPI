# SocialAPI

SocialAPI is a RESTful API for a social network application built with Node.js, Express, and MongoDB. It allows users to create accounts, post thoughts, and interact with other users by adding friends and reacting to thoughts.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Models](#models)
- [Error Handling](#error-handling)
- [License](#license)

## Installation

1. Clone the repository:
    ```sh
    git clone https://github.com/yourusername/socialapi.git
    cd socialapi
    ```

2. Install dependencies:
    ```sh
    npm install
    ```

3. Create a `.env` file in the root directory and add your MongoDB URI and other environment variables:
    ```env
    MONGODB_URI=mongodb://127.0.0.1:27017/socialnetworkapi
    PORT=3001
    NODE_ENV=development
    ```

4. Build the project:
    ```sh
    npm run build
    ```

5. Start the server:
    ```sh
    npm start
    ```

## Usage

Once the server is running, you can interact with the API using tools like Postman or cURL. The base URL for the API is `http://localhost:3001/api`.

## API Endpoints

### Users

- `GET /api/users` - Get all users
- `GET /api/users/:id` - Get a user by ID
- `POST /api/users` - Create a new user
- `PUT /api/users/:id` - Update a user by ID
- `DELETE /api/users/:id` - Delete a user by ID
- `POST /api/users/:userId/friends/:friendId` - Add a friend
- `DELETE /api/users/:userId/friends/:friendId` - Remove a friend

### Thoughts

- `GET /api/thoughts` - Get all thoughts
- `GET /api/thoughts/:id` - Get a thought by ID
- `POST /api/thoughts` - Create a new thought
- `PUT /api/thoughts/:id` - Update a thought by ID
- `DELETE /api/thoughts/:id` - Delete a thought by ID
- `POST /api/thoughts/:thoughtId/reactions` - Add a reaction to a thought
- `DELETE /api/thoughts/:thoughtId/reactions/:reactionId` - Remove a reaction from a thought

## Models

### User

- `username` (String, required, unique)
- `email` (String, required, unique)
- `thoughts` (Array of ObjectId, references Thought)
- `friends` (Array of ObjectId, references User)

### Thought

- `thoughtText` (String, required)
- `createdAt` (Date, default: Date.now)
- `username` (String, required)
- `userId` (ObjectId, references User)
- `reactions` (Array of Reaction)

### Reaction

- `reactionId` (ObjectId, default: new ObjectId())
- `reactionBody` (String, required)
- `username` (String, required)
- `createdAt` (Date, default: Date.now)

## Error Handling

Errors are handled using the `handleError` function in [`src/utils/errorHandler.ts`](src/utils/errorHandler.ts). The function logs the error and sends a JSON response with the error message and stack trace (in development mode).

## License

This project is licensed under the MIT License.

## GitHub Repo Link

https://github.com/Dsien/SocialAPI.git

