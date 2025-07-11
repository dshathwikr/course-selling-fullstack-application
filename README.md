# Course Selling Fullstack Application - API Documentation

## About the Application

The Course Selling Fullstack Application is a platform that allows administrators to create and manage online courses, and users to browse, purchase, and access these courses. The backend provides secure authentication for both admins and users, supports course management, and tracks user purchases. The application is built using Node.js, Express, MongoDB, and JWT for authentication, and is designed to be used as the backend for a modern web-based course marketplace.

## Overview

This backend provides a RESTful API for a course selling platform. It supports user and admin authentication, course management, and course purchasing. The backend is built with Node.js, Express, MongoDB, and uses JWT for authentication.

---

## Table of Contents

- [Authentication](#authentication)
- [API Endpoints](#api-endpoints)
  - [Admin Routes](#admin-routes)
  - [User Routes](#user-routes)
  - [Course Routes](#course-routes)
- [Error Handling](#error-handling)
- [Environment Variables](#environment-variables)
- [Contact](#contact)

---

## Authentication

- JWT tokens are used for authentication.
- For protected routes, add the header:  
  `Authorization: Bearer <token>`

---

## API Endpoints

### Admin Routes

#### Register Admin

- **POST** `/admin/signup`
- **Body:**
  ```json
  {
    "firstName": "John",
    "lastName": "Doe",
    "email": "admin@example.com",
    "password": "yourpassword"
  }
  ```
- **Response:**
  ```json
  { "message": "You are signed up!" }
  ```

#### Login Admin

- **POST** `/admin/signin`
- **Body:**
  ```json
  {
    "email": "admin@example.com",
    "password": "yourpassword"
  }
  ```
- **Response:**
  ```json
  { "token": "<jwt_token>" }
  ```

#### Create Course

- **POST** `/admin/course`
- **Headers:** `Authorization: Bearer <admin_token>`
- **Body:**
  ```json
  {
    "title": "Course Title",
    "description": "Course Description",
    "price": 100,
    "imageURL": "https://example.com/image.jpg"
  }
  ```
- **Response:**
  ```json
  { "message": "Course created successfully" }
  ```

#### Update Course

- **PUT** `/admin/course`
- **Headers:** `Authorization: Bearer <admin_token>`
- **Body:**
  ```json
  {
    "courseId": "<course_id>",
    "title": "Updated Title",
    "description": "Updated Description",
    "price": 120,
    "imageURL": "https://example.com/newimage.jpg"
  }
  ```
- **Response:**
  ```json
  { "message": "Course updated successfully" }
  ```

#### Get Admin's Courses

- **GET** `/admin/course`
- **Headers:** `Authorization: Bearer <admin_token>`
- **Response:**
  ```json
  [
    {
      "_id": "<course_id>",
      "title": "Course Title",
      "description": "Course Description",
      "price": 100,
      "imageURL": "https://example.com/image.jpg",
      "creatorId": "<admin_id>",
      "createdAt": "...",
      "updatedAt": "..."
    }
  ]
  ```

---

### User Routes

#### Register User

- **POST** `/user/signup`
- **Body:**
  ```json
  {
    "firstName": "Jane",
    "lastName": "Smith",
    "email": "user@example.com",
    "password": "yourpassword"
  }
  ```
- **Response:**
  ```json
  { "message": "You are signed up!" }
  ```

#### Login User

- **POST** `/user/signin`
- **Body:**
  ```json
  {
    "email": "user@example.com",
    "password": "yourpassword"
  }
  ```
- **Response:**
  ```json
  { "token": "<jwt_token>" }
  ```

#### Get Purchased Courses

- **GET** `/user/purchases`
- **Headers:** `Authorization: Bearer <user_token>`
- **Response:**
  ```json
  {
    "courses": [
      {
        "_id": "<purchase_id>",
        "userId": "<user_id>",
        "courseId": "<course_id>",
        "createdAt": "...",
        "updatedAt": "..."
      }
    ]
  }
  ```

---

### Course Routes

#### Get All Courses (Preview)

- **GET** `/course/preview`
- **Response:**
  ```json
  [
    {
      "_id": "<course_id>",
      "title": "Course Title",
      "description": "Course Description",
      "price": 100,
      "imageURL": "https://example.com/image.jpg",
      "creatorId": "<admin_id>",
      "createdAt": "...",
      "updatedAt": "..."
    }
  ]
  ```

#### Purchase Course

- **POST** `/course/purchase`
- **Headers:** `Authorization: Bearer <user_token>`
- **Body:**
  ```json
  {
    "courseId": "<course_id>"
  }
  ```
- **Response:**
  ```json
  { "message": "Purchased successfully" }
  ```

---

## Error Handling

- All errors return a JSON object with a `message` and may include an `error` field.
- Example:
  ```json
  {
    "message": "Validation failed",
    "error": [ ... ]
  }
  ```

---

## Environment Variables

| Variable           | Description                        |
|--------------------|------------------------------------|
| PORT               | Port to run the server             |
| MONGODB_URI        | MongoDB connection string          |
| JWT_SECRET_ADMIN   | JWT secret for admin tokens        |
| JWT_SECRET_USER    | JWT secret for user tokens         |

---

## Contact

For questions or support, contact [dshathwikr@gmail.com](mailto:dshathwikr@gmail.com).

---
