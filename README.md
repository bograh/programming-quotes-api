# programming-quotes-api

An api which generates quotes for programmers from programmers 🤓

## API Endpoints

### Base URL

```
http://localhost:2000
```

### Endpoints

#### 1. Get Random Quote

Returns a single random programming quote.

**Endpoint:** `GET /api/random`

**Query Parameters:**

- `author` (optional): Filter quotes by author name (case-insensitive, supports partial matching)

**Examples:**

```bash
# Get a random quote
GET /api/random

# Get a random quote by specific author
GET /api/random?author=Dijkstra
```

**Response:**

```json
{
  "author": "Edsger W. Dijkstra",
  "quote": "Computer Science is no more about computers than astronomy is about telescopes."
}
```

---

#### 2. Get Bulk Quotes

Returns 10 random programming quotes (or fewer if filtered results are less than 10).

**Endpoint:** `GET /api/bulk`

**Query Parameters:**

- `author` (optional): Filter quotes by author name (case-insensitive, supports partial matching)

**Examples:**

```bash
# Get 10 random quotes
GET /api/bulk

# Get up to 10 random quotes by specific author
GET /api/bulk?author=Martin
```

**Response:**

```json
[
  {
    "author": "Author Name",
    "quote": "Quote text here..."
  },
  {
    "author": "Another Author",
    "quote": "Another quote text..."
  }
  // ... up to 10 quotes
]
```

---

#### 3. Get Available Count

Returns the number of available quotes in the database.

**Endpoint:** `GET /api/available`

**Query Parameters:**

- `author` (optional): Get count of quotes by a specific author (case-insensitive, supports partial matching)

**Examples:**

```bash
# Get total number of quotes available
GET /api/available

# Get number of quotes by specific author
GET /api/available?author=Knuth
```

**Response:**

```
200
```

(Returns a number indicating the count of available quotes)

---

## Features

- 🔒 **Rate Limited**: 100 requests per hour
- 🌐 **CORS Enabled**: Accessible from any origin
- 🛡️ **Security Headers**: Protected with Helmet.js
- ⚡ **Fast Response**: Optimized for quick quote retrieval

## Rate Limiting

The API is rate-limited to **100 requests per hour** per IP address. If you exceed this limit, you'll receive a `429 Too Many Requests` response.

## Error Responses

The API uses standard HTTP status codes:

- `200 OK`: Successful request
- `429 Too Many Requests`: Rate limit exceeded

---

## Usage Examples

### JavaScript (Fetch API)

```javascript
// Get a random quote
fetch("https://your-api-domain.com/api/random")
  .then((response) => response.json())
  .then((data) => console.log(data));

// Get quotes by author
fetch("https://your-api-domain.com/api/random?author=Dijkstra")
  .then((response) => response.json())
  .then((data) => console.log(data));

// Get bulk quotes
fetch("https://your-api-domain.com/api/bulk")
  .then((response) => response.json())
  .then((data) => console.log(data));

// Get available count
fetch("https://your-api-domain.com/api/available")
  .then((response) => response.text())
  .then((count) => console.log(`Total quotes: ${count}`));
```

### Python (requests)

```python
import requests

# Get a random quote
response = requests.get('https://your-api-domain.com/api/random')
quote = response.json()
print(quote)

# Get quotes by author
response = requests.get('https://your-api-domain.com/api/random?author=Knuth')
quote = response.json()
print(quote)
```

### cURL

```bash
# Get a random quote
curl https://your-api-domain.com/api/random

# Get bulk quotes
curl https://your-api-domain.com/api/bulk

# Get available count
curl https://your-api-domain.com/api/available
```
