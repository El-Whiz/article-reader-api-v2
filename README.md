# Blog API

A RESTful Blog API with JWT authentication, built with Express + MongoDB.

## Stack
- **Express** — web framework
- **Mongoose** — MongoDB ODM
- **bcryptjs** — password hashing
- **jsonwebtoken** — JWT auth

---

## Project Structure
```
blog-api/
├── src/
│   ├── index.js            # Entry point
│   ├── middleware/
│   │   └── auth.js         # JWT middleware
│   ├── models/
│   │   ├── User.js
│   │   └── Post.js
│   └── routes/
│       ├── auth.js
│       └── posts.js
├── package.json
├── render.yaml
└── .gitignore
```

---

## Local Setup

```bash
npm install

# Create .env
MONGODB_URI=mongodb+srv://<user>:<pass>@cluster.mongodb.net/blogdb
JWT_SECRET=your_super_secret_key

npm run dev
```

---

## API Endpoints

### Auth
| Method | Endpoint | Body | Auth |
|--------|----------|------|------|
| POST | `/api/auth/register` | `{username, email, password}` | No |
| POST | `/api/auth/login` | `{email, password}` | No |

### Posts
| Method | Endpoint | Body | Auth |
|--------|----------|------|------|
| GET | `/api/posts` | — | No |
| GET | `/api/posts/:id` | — | No |
| POST | `/api/posts` | `{title, content}` | ✅ Bearer token |
| PUT | `/api/posts/:id` | `{title?, content?}` | ✅ Owner only |
| DELETE | `/api/posts/:id` | — | ✅ Owner only |

**Authorization header format:**
```
Authorization: Bearer <your_jwt_token>
```

---

## Deploy to Render

1. Push code to a GitHub repo
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your GitHub repo
4. Render auto-detects `render.yaml` — or set manually:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
5. Add **Environment Variables** in Render dashboard:
   - `MONGODB_URI` — your MongoDB Atlas connection string
   - `JWT_SECRET` — a long random string

> **MongoDB Atlas free tier:** [mongodb.com/atlas](https://mongodb.com/atlas) — create a cluster, whitelist `0.0.0.0/0` for Render access.

---

## Example Usage

```bash
# Register
curl -X POST https://your-app.onrender.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"alice","email":"alice@example.com","password":"secret123"}'

# Login
curl -X POST https://your-app.onrender.com/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"alice@example.com","password":"secret123"}'

# Create post (use token from login response)
curl -X POST https://your-app.onrender.com/api/posts \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"title":"My First Post","content":"Hello world!"}'
```# Blog API

A RESTful Blog API with JWT authentication, built with Express + MongoDB.

## Stack
- **Express** — web framework
- **Mongoose** — MongoDB ODM
- **bcryptjs** — password hashing
- **jsonwebtoken** — JWT auth

---

## Project Structure
```
blog-api/
├── src/
│   ├── index.js            # Entry point
│   ├── middleware/
│   │   └── auth.js         # JWT middleware
│   ├── models/
│   │   ├── User.js
│   │   └── Post.js
│   └── routes/
│       ├── auth.js
│       └── posts.js
├── package.json
├── render.yaml
└── .gitignore
```

---

## Local Setup

```bash
npm install

# Create .env
MONGODB_URI=mongodb+srv://<user>:<pass>@cluster.mongodb.net/blogdb
JWT_SECRET=your_super_secret_key

npm run dev
```

---

## API Endpoints

### Auth
| Method | Endpoint | Body | Auth |
|--------|----------|------|------|
| POST | `/api/auth/register` | `{username, email, password}` | No |
| POST | `/api/auth/login` | `{email, password}` | No |

### Posts
| Method | Endpoint | Body | Auth |
|--------|----------|------|------|
| GET | `/api/posts` | — | No |
| GET | `/api/posts/:id` | — | No |
| POST | `/api/posts` | `{title, content}` | ✅ Bearer token |
| PUT | `/api/posts/:id` | `{title?, content?}` | ✅ Owner only |
| DELETE | `/api/posts/:id` | — | ✅ Owner only |

**Authorization header format:**
```
Authorization: Bearer <your_jwt_token>
```

---

## Deploy to Render

1. Push code to a GitHub repo
2. Go to [render.com](https://render.com) → **New Web Service**
3. Connect your GitHub repo
4. Render auto-detects `render.yaml` — or set manually:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
5. Add **Environment Variables** in Render dashboard:
   - `MONGODB_URI` — your MongoDB Atlas connection string
   - `JWT_SECRET` — a long random string

> **MongoDB Atlas free tier:** [mongodb.com/atlas](https://mongodb.com/atlas) — create a cluster, whitelist `0.0.0.0/0` for Render access.

---

## Example Usage

```bash
# Register
curl -X POST https://your-app.onrender.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"alice","email":"alice@example.com","password":"secret123"}'

# Login
curl -X POST https://your-app.onrender.com/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"alice@example.com","password":"secret123"}'

# Create post (use token from login response)
curl -X POST https://your-app.onrender.com/api/posts \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <token>" \
  -d '{"title":"My First Post","content":"Hello world!"}'
```
