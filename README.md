# Search API Assignment

---

## 📮 Postman Documentation

https://documenter.getpostman.com/view/50839289/2sBXwpPX2X

---

## 💻 GitHub Repository

 https://github.com/VishwaPatel892/Crud_Assignment3

---

## 📌 Objective

This project is a **REST API built using Express.js** that manages notes using **MongoDB with Mongoose**.

The API extends CRUD functionality by introducing:

* Search APIs using MongoDB `$regex`
* Combined query operations
* Search + Filter
* Search + Sort
* Search + Pagination
* Filter + Sort + Pagination
* Master Query Endpoint

---

## 🚀 Features

### CRUD Operations

* Create single note
* Create multiple notes
* Get all notes
* Get note by ID
* Replace note
* Update note partially
* Delete single note
* Delete multiple notes

### Search APIs

* Search by title
* Search by content
* Search by title and content

### Combined Queries

* Filter + Sort
* Filter + Pagination
* Sort + Pagination
* Search + Filter
* Search + Sort + Pagination
* Filter + Sort + Pagination

### Master Query API

* Search
* Filter
* Sort
* Pagination
* All concepts combined in one endpoint

---

## 🛠️ Tech Stack

* Node.js
* Express.js
* MongoDB
* Mongoose
* Postman

---

## 📂 Project Structure

```text
notes-app/
│
├── src/
│   ├── config/
│   │   └── db.js
│   │
│   ├── models/
│   │   └── note.model.js
│   │
│   ├── controllers/
│   │   └── note.controller.js
│   │
│   ├── routes/
│   │   └── note.routes.js
│   │
│   ├── middlewares/
│   │
│   ├── app.js
│   └── index.js
│
├── .env
├── .env.example
└── package.json
```

---

# API Endpoints

Base URL:

```text
/api/notes
```

---

## CRUD Endpoints

| Method | Endpoint          | Description             |
| ------ | ----------------- | ----------------------- |
| POST   | `/api/notes`      | Create single note      |
| POST   | `/api/notes/bulk` | Create multiple notes   |
| GET    | `/api/notes`      | Get all notes           |
| GET    | `/api/notes/:id`  | Get note by ID          |
| PUT    | `/api/notes/:id`  | Replace note completely |
| PATCH  | `/api/notes/:id`  | Update specific fields  |
| DELETE | `/api/notes/:id`  | Delete single note      |
| DELETE | `/api/notes/bulk` | Delete multiple notes   |

---

## Search Endpoints

| Method | Endpoint                              | Description                 |
| ------ | ------------------------------------- | --------------------------- |
| GET    | `/api/notes/search?q=keyword`         | Search in title             |
| GET    | `/api/notes/search/content?q=keyword` | Search in content           |
| GET    | `/api/notes/search/all?q=keyword`     | Search in title and content |

---

## Two Concepts Combined

| Method | Endpoint                     | Description         |
| ------ | ---------------------------- | ------------------- |
| GET    | `/api/notes/filter-sort`     | Filter + Sort       |
| GET    | `/api/notes/filter-paginate` | Filter + Pagination |
| GET    | `/api/notes/sort-paginate`   | Sort + Pagination   |
| GET    | `/api/notes/search-filter`   | Search + Filter     |

---

## Three Concepts Combined

| Method | Endpoint                          | Description                |
| ------ | --------------------------------- | -------------------------- |
| GET    | `/api/notes/search-sort-paginate` | Search + Sort + Pagination |
| GET    | `/api/notes/filter-sort-paginate` | Filter + Sort + Pagination |

---

## Master Endpoint

| Method | Endpoint           | Description                         |
| ------ | ------------------ | ----------------------------------- |
| GET    | `/api/notes/query` | Search + Filter + Sort + Pagination |

---

# Search Examples

## Search Title

```http
GET /api/notes/search?q=node
```

```http
GET /api/notes/search?q=meeting
```

---

## Search Content

```http
GET /api/notes/search/content?q=deployment
```

```http
GET /api/notes/search/content?q=react
```

---

## Search Title & Content

```http
GET /api/notes/search/all?q=node
```

```http
GET /api/notes/search/all?q=meeting
```

---

# Combined Query Examples

## Filter + Sort

```http
GET /api/notes/filter-sort?category=work&sortBy=title&order=asc
```

---

## Filter + Pagination

```http
GET /api/notes/filter-paginate?category=work&page=1&limit=5
```

---

## Sort + Pagination

```http
GET /api/notes/sort-paginate?sortBy=createdAt&order=desc&page=1&limit=5
```

---

## Search + Filter

```http
GET /api/notes/search-filter?q=meeting&category=work
```

---

## Search + Sort + Pagination

```http
GET /api/notes/search-sort-paginate?q=node&sortBy=title&order=asc&page=1&limit=5
```

---

## Filter + Sort + Pagination

```http
GET /api/notes/filter-sort-paginate?category=study&sortBy=title&order=asc&page=1&limit=5
```

---

# Master Query Examples

## Search Only

```http
GET /api/notes/query?q=react
```

---

## Filter Only

```http
GET /api/notes/query?category=work
```

---

## Sort Only

```http
GET /api/notes/query?sortBy=title&order=asc
```

---

## Pagination Only

```http
GET /api/notes/query?page=2&limit=5
```

---

## Everything Together

```http
GET /api/notes/query?q=node&category=study&isPinned=false&sortBy=updatedAt&order=desc&page=2&limit=3
```

---

# Response Format

Every endpoint follows the same structure:

```json
{
  "success": true,
  "message": "Operation successful",
  "data": []
}
```

---

## List Response

```json
{
  "success": true,
  "message": "Notes fetched successfully",
  "count": 10,
  "data": []
}
```

---

## Pagination Response

```json
{
  "success": true,
  "message": "Notes fetched successfully",
  "data": [],
  "pagination": {
    "total": 25,
    "page": 1,
    "limit": 5,
    "totalPages": 5,
    "hasNextPage": true,
    "hasPrevPage": false
  }
}
```

---

# Validation Rules

### Create Note

* Title is required
* Content is required

### Bulk Create

* notes array must exist
* notes array cannot be empty

### Search APIs

* `q` query parameter is required

### PATCH

* Request body cannot be empty

### Bulk Delete

* ids array must exist
* ids array cannot be empty

### ID Routes

* Validate MongoDB ObjectId
* Return 400 if invalid
* Return 404 if note not found

---

# HTTP Status Codes

| Code | Description                        |
| ---- | ---------------------------------- |
| 200  | Successful GET, PUT, PATCH, DELETE |
| 201  | Successful POST                    |
| 400  | Validation Error                   |
| 404  | Resource Not Found                 |
| 500  | Internal Server Error              |

---

# Environment Variables

### .env

```env
MONGO_URI=your_mongodb_connection_string
PORT=5000
```

### .env.example

```env
MONGO_URI=your_mongodb_connection_string_here
PORT=5000
```

---

# Installation

### Clone Repository

```bash
git clone https://github.com/your-username/Search_API_Assignment.git
```

### Move into Project Directory

```bash
cd notes-app
```

### Install Dependencies

```bash
npm install
```

### Run Development Server

```bash
npm run dev
```

### Run Production Server

```bash
npm start
```

Server runs on:

```text
http://localhost:5000
```

---

# Required Packages

```bash
npm install express mongoose dotenv
npm install --save-dev nodemon
```

---

# Submission

### Submit the Following

1. GitHub Repository Link
2. Postman Documentation Link
3. Live Backend Deployment Link

---

## Author

**Vishwa Patel**

Assignment 03 – Search APIs & Combined Queries

Node.js • Express.js • MongoDB • Mongoose
