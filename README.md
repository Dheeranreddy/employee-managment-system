# 🧑‍💼 Employee Management System

A simple and responsive **Employee Management Web Application** built using **Vue.js, Axios, and MockAPI**.  
This project demonstrates full **CRUD (Create, Read, Update, Delete)** operations with a clean and responsive **Bootstrap UI**.

---

## 🚀 Features

- ➕ Add new employee records
- 📋 View all employees in a table
- ✏️ Update employee details
- ❌ Delete employee records
- 📱 Responsive UI using Bootstrap
- 🔄 Real-time API interaction using Axios

---

## 🛠️ Tech Stack

- **Frontend:** Vue.js
- **HTTP Client:** Axios
- **Backend (Mock):** MockAPI
- **Styling:** Bootstrap

---

## 📂 Project Structure

```
src/
├── components/
│   ├── AddEmployee.vue
│   ├── ViewEmployee.vue
│   ├── UpdateEmployee.vue
│   ├── DeleteEmployee.vue
├── App.vue
├── main.js
```

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Dheeranreddy/employee-managment-system
cd Employee-Management-System
```

### 2️⃣ Install Dependencies

```bash
npm install
```

### 3️⃣ Install Required Packages

```bash
npm install axios bootstrap
```

### ▶️ Run the Application

```bash
npm run serve
```

Open in browser:  
[http://localhost:8080](http://localhost:8080)

---

## 🌐 API Configuration

This project uses MockAPI as backend.

**Example Endpoint:**  
`https://69f8cc42f7044aa0103e80c0.mockapi.io/assig-2`

### Employee Fields

- **ID** (auto-generated)
- **Name**
- **Designation**
- **Department**
- **Salary**

---

## 🔄 CRUD Operations

| Operation | Method | Description             |
| --------- | ------ | ----------------------- |
| Create    | POST   | Add new employee        |
| Read      | GET    | Fetch all employees     |
| Update    | PUT    | Modify employee details |
| Delete    | DELETE | Remove employee         |

---

## 🎯 Key Concepts Used

- Vue Components (Reusable structure)
- Two-way Data Binding (`v-model`)
- Directives (`v-for`, `v-if`)
- Lifecycle Hooks (`mounted()`)
- Axios for API calls
- Async operations handling

---

## 💡 Future Improvements

- 🔍 Add search & filter functionality
- ✅ Add form validation
- 🎨 Improve UI with cards or modals
- 🔐 Add authentication system

---

## 📸 Output

- Functional CRUD application
- Responsive layout
- Real-time updates from API
