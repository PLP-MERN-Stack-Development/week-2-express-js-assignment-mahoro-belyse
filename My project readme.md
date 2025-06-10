# Product API (Express.js)

This is a basic Express.js RESTful API for managing a simple in-memory product list. It includes product CRUD operations, basic authentication, request logging, and validation.

## 📁 Project Structure

```
.
├── dede.js           # Minimal Hello World Express server
├── server.js         # Main API server with full CRUD functionality
├── .env.example      # Example environment variable file
└── README.md         # Project documentation
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v14+ recommended)
- npm (Node package manager)

### Installation

1. Clone the repository or download the files.
2. Navigate into the project directory.
3. Install dependencies:

```bash
npm install express body-parser uuid
```

4. Create a `.env` file based on `.env.example`:

```env
PORT=3000
API_KEY=my-secret-key
```

> Note: The current implementation uses hardcoded API key authentication in `server.js`. The `.env` variables are not yet wired into the code.

### Run the Server

To start the minimal "Hello World" server:

```bash
node dede.js
```

To start the main Product API server:

```bash
node server.js
```

By default, the API runs at http://localhost:3000.

## 📡 API Endpoints

### Public Routes

- `GET /`  
  Welcome message and instructions.

- `GET /api/products`  
  Returns all products.

- `GET /api/products/:id`  
  Returns a single product by ID.

### Protected Routes (Require API Key)

Include header:  
`x-api-key: my-secret-key`

- `POST /api/products`  
  Create a new product. Requires valid product fields.

- `PUT /api/products/:id`  
  Update an existing product.

- `DELETE /api/products/:id`  
  Delete a product by ID.

## 🛡 Middleware Features

- **Logging**: Logs every request with a timestamp.
- **Authentication**: Verifies API key via the `x-api-key` header.
- **Validation**: Ensures required fields are present and correct in POST/PUT requests.
- **Error Handling**: Centralized error handler for unexpected issues.

## 📦 Example Product Format

```json
{
  "name": "Headphones",
  "description": "Noise-cancelling headphones",
  "price": 250,
  "category": "electronics",
  "inStock": true
}
```

## 🧪 Testing

Use tools like Postman or curl to test endpoints. Example:

```bash
curl -X POST http://localhost:3000/api/products \
-H "Content-Type: application/json" \
-H "x-api-key: my-secret-key" \
-d '{
  "name": "Blender",
  "description": "High-speed kitchen blender",
  "price": 99,
  "category": "kitchen",
  "inStock": true
}'
```

## 🔒 Notes

- Products are stored in memory. Restarting the server resets the product list.
- The API key is hardcoded in the source file (`my-secret-key`).
- `.env` support can be added using the `dotenv` package.
