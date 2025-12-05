# Express.js Learning Project: Startups API

This project represents my introduction to backend development with Node.js and Express. It is a RESTful API that manages a dataset of startups, demonstrating core concepts of server-side programming.

## 🚀 What I Learned
This project covers the fundamental building blocks of Express.js:
- **Creating a Server**: Setting up an Express application from scratch.
- **Request & Response Handling**: Understanding the HTTP cycle.
- **Query Parameters**: Filtering data dynamically (e.g., `?industry=tech`).
- **Path Parameters**: Building dynamic routes (e.g., `/api/:category/:id`).
- **Status Codes**: Managing HTTP responses (200, 404, etc.).
- **CORS**: Handling Cross-Origin Resource Sharing.

## 🛠️ Installation & Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run the server**
   ```bash
   # If using nodemon
   npm run dev
   
   # Standard node
   node index.js
   ```

4. **Visit the API**
   Open `http://localhost:8000/api` in your browser.

## 📡 API Endpoints

### 1. Filter Startups (Query Params)
Filter the full list of startups using multiple criteria simultaneously.

**Endpoint:** `GET /api`

**Parameters:**
- `industry` (string)
- `country` (string)
- `continent` (string)
- `has_mvp` (boolean)
- `is_seeking_funding` (boolean)

**Example:**
```
GET /api?industry=biotech&country=germany&has_mvp=true
```

### 2. Dynamic Search (Path Params)
Search for startups by specifying the field and the value directly in the URL.

**Endpoint:** `GET /api/:field/:term`

**Examples:**
- Get all startups in India:
  `GET /api/country/india`
- Get all startups in the AI industry:
  `GET /api/industry/ai`

## 🧩 Code Highlight
One of the key challenges solved in this project was implementing dynamic property access to filter data based on URL parameters without writing repetitive `if/else` blocks.

```javascript
app.get('/api/:field/:term', (req, res) => {
  const { field, term } = req.params
  
  // Dynamic bracket notation to access object properties
  const filteredData = startups.filter(startup => {
    return startup[field].toLowerCase() === term.toLowerCase()
  })
  
  res.json(filteredData)
})
```

## 📝 License
This project is for educational purposes.
