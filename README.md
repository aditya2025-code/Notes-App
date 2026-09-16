<div align="center">

# 📝 Notes App

### A simple, lightweight and practical note management web application built with Node.js and Express.js.

Create. Read. Rename. Organize.
A small project built to understand the fundamentals of backend web development.

<br>

[![GitHub](https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge\&logo=github)](https://github.com/aditya2025-code/Notes-App)
[![Node.js](https://img.shields.io/badge/Node.js-Runtime-339933?style=for-the-badge\&logo=node.js\&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express.js-Framework-000000?style=for-the-badge\&logo=express)](https://expressjs.com/)
[![EJS](https://img.shields.io/badge/EJS-Templates-B4CA65?style=for-the-badge\&logo=ejs\&logoColor=black)](https://ejs.co/)

<br>

**⭐ If you find this project useful, consider giving it a star!**

</div>

---

## 📸 Screenshots

### 🏠 Home Page

<!-- Replace this path after adding your screenshot -->

![Home Page](./screenshots/home.png)

### 📖 Note View

<!-- Replace this path after adding your screenshot -->

![Note View](./screenshots/note-view.png)

### ✏️ Edit Note

<!-- Replace this path after adding your screenshot -->

![Edit Note](./screenshots/edit-note.png)

---

## 🎯 Why This Project?

**Notes App** is my first Express.js web application.

The idea was intentionally simple:

> Build something small enough to understand completely, but useful enough that someone could actually use it.

Instead of jumping directly into a large full-stack application, this project focuses on understanding the fundamentals behind an Express application:

* HTTP requests and responses
* Express routing
* Form handling
* EJS server-side rendering
* Static files
* Node.js File System operations
* Dynamic URLs
* Creating and reading files
* Renaming files
* Basic CRUD concepts

The application currently stores notes as `.txt` files, making the project simple and easy to understand while learning backend development.

---

# ✨ Features

<div align="center">

|     📝 Create    |      📖 Read     |   ✏️ Rename  | 📂 File Storage |
| :--------------: | :--------------: | :----------: | :-------------: |
| Create new notes | Read saved notes | Rename notes | Store as `.txt` |

|    ⚡ Express    |     🎨 EJS    | 📁 Static Files | 🚀 Deployment Ready |
| :-------------: | :-----------: | :-------------: | :-----------------: |
| Backend routing | Dynamic pages |    CSS/assets   |  Vercel compatible  |

</div>

### Current Functionality

* 📝 Create a new note
* 📖 View existing notes
* ✏️ Rename existing notes
* 📂 Store notes inside the `files/` directory
* 🔄 Dynamically display available notes
* 🎨 Serve static frontend assets
* 🧩 Render pages using EJS
* 🌐 Run locally or on a deployment platform

---

# 🧰 Tech Stack

| Technology          | Role                   |
| ------------------- | ---------------------- |
| 🟢 **Node.js**      | JavaScript runtime     |
| ⚡ **Express.js**    | Backend web framework  |
| 🎨 **EJS**          | Server-side templating |
| 📄 **HTML**         | Page structure         |
| 🎨 **CSS**          | User interface styling |
| 📁 **Node.js `fs`** | File operations        |
| 🔀 **Git**          | Version control        |
| 🐙 **GitHub**       | Source code hosting    |
| ▲ **Vercel**        | Deployment             |

The current project uses Express `5.2.1` and EJS `6.0.1`.

---

# 🏗️ Project Architecture

```text
                         ┌─────────────────────┐
                         │       Browser       │
                         │                     │
                         │  HTML / CSS / Forms │
                         └──────────┬──────────┘
                                    │
                                    │ HTTP Request
                                    ▼
                         ┌─────────────────────┐
                         │     Express.js      │
                         │                     │
                         │      index.js       │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┼───────────────┐
                    │               │               │
                    ▼               ▼               ▼
              ┌──────────┐   ┌───────────┐   ┌──────────┐
              │  Routes  │   │    EJS    │   │ Node fs  │
              │          │   │ Templates │   │ File API │
              └──────────┘   └───────────┘   └────┬─────┘
                                                  │
                                                  ▼
                                           ┌──────────────┐
                                           │    files/    │
                                           │              │
                                           │ *.txt notes  │
                                           └──────────────┘
```

### Request Flow

```text
User
  │
  ▼
Browser
  │
  │ GET / POST
  ▼
Express Server
  │
  ├── Route Handler
  │
  ├── File System Operation
  │
  └── EJS Template
          │
          ▼
      HTML Response
          │
          ▼
        Browser
```

---

# 📁 Project Structure

```text
Notes-App/
│
├── 📂 files/
│   └── 📝 *.txt
│       └── Notes stored as text files
│
├── 📂 public/
│   └── 🎨 Static assets
│       └── CSS / frontend resources
│
├── 📂 views/
│   ├── 🏠 index.ejs
│   ├── 📖 show.ejs
│   └── ✏️ edit.ejs
│
├── 📄 index.js
│   └── Main Express application
│
├── 📄 package.json
│   └── Project configuration
│
├── 📄 package-lock.json
│   └── Locked dependency versions
│
└── 📄 .gitignore
    └── Ignored files
```

The repository currently follows this basic structure with `files`, `public`, `views`, `index.js`, `package.json`, and related project files.

---

# 🔌 API / Route Reference

The application currently has a small and easy-to-understand route structure.

| Method | Route             | Purpose                     |
| ------ | ----------------- | --------------------------- |
| `GET`  | `/`               | Display all available notes |
| `GET`  | `/file/:filename` | View a specific note        |
| `GET`  | `/edit/:filename` | Open the rename page        |
| `POST` | `/edit`           | Rename an existing note     |
| `POST` | `/create`         | Create a new note           |

---

## `GET /`

Displays the main Notes App page.

The server reads the `files/` directory and passes the available files to the EJS template.

```text
Browser
   ↓
GET /
   ↓
Express
   ↓
fs.readdir()
   ↓
index.ejs
   ↓
HTML response
```

---

## `GET /file/:filename`

Displays the content of a selected note.

Example:

```text
/file/JavaNotes.txt
```

The server reads the requested file and renders it using `show.ejs`.

---

## `GET /edit/:filename`

Opens the edit/rename page for a selected note.

Example:

```text
/edit/JavaNotes.txt
```

The filename is passed to the EJS template.

---

## `POST /edit`

Renames an existing note.

The request contains:

```text
Previous
New
```

The server then uses Node's file-system functionality to rename the file.

---

## `POST /create`

Creates a new note.

The request contains:

```text
title
details
```

The application creates a `.txt` file inside:

```text
files/
```

The current implementation creates the filename from the submitted title and stores the submitted details as the file contents.

---

# ⚙️ How To Run Locally

## 1️⃣ Prerequisites

Make sure you have installed:

* Node.js
* npm
* Git

Check your installation:

```bash
node -v
```

```bash
npm -v
```

```bash
git --version
```

---

## 2️⃣ Clone the Repository

```bash
git clone https://github.com/aditya2025-code/Notes-App.git
```

Move into the project:

```bash
cd Notes-App
```

---

## 3️⃣ Install Dependencies

```bash
npm install
```

This installs the dependencies defined in `package.json`.

---

## 4️⃣ Start the Application

```bash
npm start
```

The application uses:

```text
node index.js
```

as its start command.

---

## 5️⃣ Open in Your Browser

For local development, open:

```text
http://localhost:6969
```

The server uses the environment-provided `PORT` when available and falls back to port `6969`.

---

# 💾 How Notes Are Stored

This project intentionally uses the Node.js File System instead of a database.

For example:

```text
files/
│
├── Java.txt
├── DBMS.txt
├── Ideas.txt
└── Todo.txt
```

Each note is simply a text file.

This approach keeps the project lightweight and makes the underlying backend logic easy to understand.

---

# 🧠 What I Learned From This Project

Building this project helped me understand the fundamentals of backend development with Node.js.

### Backend

* Node.js
* Express.js
* Routing
* HTTP methods
* Request and response objects
* Middleware
* Form data
* URL parameters
* Static files

### Server-Side Rendering

* EJS
* Dynamic data
* EJS templates
* Rendering server data into HTML

### File System

* Reading directories
* Reading files
* Creating files
* Renaming files

### Development

* npm
* package.json
* Git
* GitHub
* Deployment

---

# 🔮 Future Roadmap

The current version is intentionally simple. The next versions can gradually transform it into a complete note management platform.

## Phase 1 • Better Note Management

* [ ] Delete notes
* [ ] Edit note content
* [ ] Search notes
* [ ] Pin important notes
* [ ] Sort notes
* [ ] Add created/updated timestamps

---

## Phase 2 • Better Organization

* [ ] Categories
* [ ] Tags
* [ ] Folders
* [ ] Favorites
* [ ] Recently viewed notes
* [ ] Archive notes

---

## Phase 3 • Database

Replace `.txt` file storage with a proper database.

Potential options:

```text
MongoDB
PostgreSQL
MySQL
SQLite
```

This would allow the application to scale beyond simple local file storage.

---

## Phase 4 • Authentication

Add user accounts:

```text
Register
   ↓
Login
   ↓
Dashboard
   ↓
Personal Notes
```

Possible features:

* [ ] User registration
* [ ] Login/logout
* [ ] Password hashing
* [ ] Sessions
* [ ] User-specific notes
* [ ] Authorization

---

## Phase 5 • Modern Editor

Upgrade the note editor with:

* [ ] Markdown support
* [ ] Rich text editing
* [ ] Code blocks
* [ ] Syntax highlighting
* [ ] Image attachments
* [ ] Auto-save

---

## Phase 6 • AI Features 🤖

The project could eventually evolve into an AI-powered knowledge management application.

Possible features:

```text
                 ┌──────────────────┐
                 │    Your Notes    │
                 └────────┬─────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │    AI Engine     │
                 └────────┬─────────┘
                          │
          ┌───────────────┼───────────────┐
          ▼               ▼               ▼
      Summarize       Explain          Generate
       Notes           Notes           Flashcards
```

Potential features:

* [ ] Summarize notes
* [ ] Ask questions about notes
* [ ] Generate flashcards
* [ ] Generate quizzes
* [ ] Explain difficult concepts
* [ ] Find related notes
* [ ] AI-powered search
* [ ] Automatic tagging

---

# 🛡️ Future Security Improvements

As the application becomes multi-user, security will become increasingly important.

Planned improvements:

* [ ] Input validation
* [ ] Input sanitization
* [ ] Path traversal protection
* [ ] Authentication
* [ ] Authorization
* [ ] Secure sessions
* [ ] Rate limiting
* [ ] Error handling
* [ ] Security headers
* [ ] Database security

---

# 🧪 Development Philosophy

This project follows a simple idea:

> **Start simple. Understand everything. Then scale.**

Instead of building a huge application with dozens of libraries, this project focuses on understanding what happens underneath.

For example:

```text
Form
 ↓
POST Request
 ↓
Express Route
 ↓
Node.js fs
 ↓
File
 ↓
Redirect
 ↓
Updated UI
```

Understanding this flow makes it easier to move toward larger applications later.

---

# 📈 Project Evolution

```text
                    CURRENT
                       │
                       ▼
              ┌─────────────────┐
              │   File Storage  │
              │      Notes      │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Better CRUD     │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │    Database     │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Authentication  │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │  User Accounts  │
              └────────┬────────┘
                       │
                       ▼
              ┌─────────────────┐
              │   AI Features   │
              └─────────────────┘
```

---

# 🤝 Contributing

Contributions and suggestions are welcome!

### Fork the repository

```bash
git fork
```

Or use the **Fork** button on GitHub.

### Clone your fork

```bash
git clone <your-fork-url>
```

### Create a feature branch

```bash
git checkout -b feature/your-feature
```

### Make your changes

```bash
git add .
```

### Commit

```bash
git commit -m "feat: add your feature"
```

### Push

```bash
git push origin feature/your-feature
```

Then open a Pull Request.

---

# 🐛 Found a Bug?

If you find a bug or have an idea for improvement:

1. Open an issue.
2. Explain the problem.
3. Include steps to reproduce it.
4. Add screenshots or error logs when useful.

---

# 👨‍💻 Author

<div align="center">

### Aditya Das

**BCA Student • Developer • Builder**

I am currently learning backend and full-stack development by building practical projects and gradually increasing their complexity.

<br>

[![GitHub](https://img.shields.io/badge/GitHub-aditya2025--code-black?style=for-the-badge\&logo=github)](https://github.com/aditya2025-code)

</div>

---

# ⭐ Support the Project

If this project helped you learn something or you simply found it useful:

### ⭐ Star the repository

### 🍴 Fork it

### 🐛 Report bugs

### 💡 Suggest improvements

Every project starts with a small idea.

This one started with a simple question:

> **"Can I build something useful with Express?"**

And this is the result. 🚀

---

<div align="center">

### 📝 Notes App

**Built with Node.js + Express.js + EJS**

Made with curiosity, code, and a lot of `console.log()`.

<br>

⭐ **Keep building. Keep learning. Keep shipping.**

</div>
