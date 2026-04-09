# Medi Rakshak 🏥
### Healthcare Access Platform — HTML/CSS/JS + Node.js + MySQL

---

## 📁 File Structure

```
medi-rakshak/
├── server.js          ← Express backend (API + session)
├── package.json       ← Node dependencies
├── database.sql       ← MySQL schema + seed data
├── README.md
└── public/
    ├── index.html     ← Single-page frontend
    ├── style.css      ← All styles
    └── app.js         ← All frontend JS
```

---

## ⚙️ Setup Instructions

### 1. Install Node.js
Download from https://nodejs.org (v18+ recommended)

### 2. Install MySQL
Download from https://dev.mysql.com/downloads/mysql/
Start the MySQL server and note your root password.

### 3. Create the Database
Open MySQL terminal and run:
```bash
mysql -u root -p < database.sql
```
This creates the `medi_rakshak` database with all tables and seed data.

### 4. Configure Database Password
Open `server.js` and update line ~20:
```js
password: process.env.DB_PASS || '',   // ← put your MySQL password here
```
Or use environment variables (recommended for production):
```bash
export DB_PASS=your_mysql_password
```

### 5. Install Dependencies
```bash
cd medi-rakshak
npm install
```

### 6. Start the Server
```bash
node server.js
# OR for auto-reload during development:
npx nodemon server.js
```

### 7. Open in Browser
Visit: **http://localhost:3000**

---

## 🔑 Demo Accounts

| Role    | Email                          | Password  |
|---------|--------------------------------|-----------|
| Admin   | admin@medirakshak.com          | admin123  |
| Patient | ravi@example.com               | pass123   |
| Doctor  | dr.ananya@medirakshak.com      | admin123  |

---

## 🛠️ Tech Stack

| Layer     | Technology                    |
|-----------|-------------------------------|
| Frontend  | HTML5, CSS3, Vanilla JS       |
| Backend   | Node.js + Express.js          |
| Database  | MySQL 8+ via mysql2 driver    |
| Auth      | bcryptjs + express-session    |
| Hosting   | Any Node.js host (Railway, Render, VPS) |

---

## 📦 API Endpoints

| Method | Route                          | Description               |
|--------|--------------------------------|---------------------------|
| GET    | /api/me                        | Get current session user  |
| POST   | /api/register                  | Register new user         |
| POST   | /api/login                     | Login                     |
| POST   | /api/logout                    | Logout                    |
| GET    | /api/doctors                   | List all doctors          |
| GET    | /api/appointments              | Get user appointments     |
| POST   | /api/appointments              | Book appointment          |
| PATCH  | /api/appointments/:id/cancel   | Cancel appointment        |
| GET    | /api/medicines?q=              | Search medicines          |
| GET    | /api/orders                    | Get orders                |
| POST   | /api/orders                    | Place order               |
| PATCH  | /api/orders/:id/status         | Update order status       |
| GET    | /api/prescriptions             | Get prescriptions         |
| POST   | /api/prescriptions/verify      | LASA/interaction check    |
| POST   | /api/telemedicine              | Schedule telemedicine     |
| POST   | /api/contact                   | Submit contact form       |
| GET    | /api/contacts                  | Admin: view messages      |
| GET    | /api/stats                     | Admin: platform stats     |

---

## 🔧 Common Issues

**"Cannot connect to MySQL"**
→ Make sure MySQL server is running: `sudo service mysql start`
→ Check your password in server.js

**"Database not found"**
→ Run `mysql -u root -p < database.sql` again

**"Port 3000 in use"**
→ Change PORT in server.js or: `PORT=4000 node server.js`

**Passwords not matching for demo accounts**
→ Re-generate hashes: `node -e "const b=require('bcryptjs');console.log(b.hashSync('admin123',10))"`
→ Update the INSERT statements in database.sql and re-run
