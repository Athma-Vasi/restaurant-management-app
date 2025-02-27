# Restaurant Management App

This is a Vue 3 application built using Options API for managing restaurants. The app communicates with a mock backend powered by <mark>json-server</mark>

## Features

    - Login
    - Register
    - Add a new restaurant
    - Update restaurant details
    - Logout


### Components

    - Login.vue
    - SignUp.vue
    - Add.vue
    - Update.vue
    - Header.vue
    - Home.vue
    
### Views

    - Home.vue
    - Login.vue
    - SignUp.vue
    - Add.vue
    - Update.vue

### Routes

    - /: Home
    - /login: Login
    - /register: SignUp
    - /add: Add
    - /update: Update

### Mock Api Endpoints

    - GET /restaurants: List all restaurants.
    - POST /restaurants: Add a new restaurant.
    - PUT /restaurants/:id: Update an existing restaurant.
    - POST /login: User login (send username and password).
    - POST /register: Register a new user (send username, email, and password).

### Future Improvements

    - Add authentication using JWT tokens.
    - Implement proper validation and error handling.
    - Add more advanced features such as restaurant reviews, ratings, etc.

### License

This project is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).

