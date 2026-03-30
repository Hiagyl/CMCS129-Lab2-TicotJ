# 🐾 Project Pawradise: Campus Pet Inventory

**Project Pawradise** is a web-based inventory system built with Laravel to track and manage community-owned pets (cats/dogs) found around a university campus. It allows users to document pet locations, physical traits, and personalities to ensure their well-being and visibility within the campus community.

---

## 🚀 Features

* **Full CRUD Lifecycle:** Create, Read, Update, and Archive pet records seamlessly.
* **Intelligent Archiving:** Utilizes Laravel **Soft Deletes** to hide pets from the main inventory without losing historical data or records.
* **Image Processing:** A dedicated **Service Layer** for handling high-quality pet photo uploads, ensuring clean storage management.
* **Responsive UI:** A modern, "Paw-themed" interface built with **Tailwind CSS** and reusable **Blade Components**.
* **Pagination:** Efficient data handling to ensure fast load times for large campus pet populations.

---

## 🛠️ Installation & Setup

### 1. Prerequisites
* **PHP 8.2+**
* **Composer**
* **Node.js & NPM**
* **PostgreSQL**

### 2. Clone and Install
```bash
# Clone the repository
git clone <your-repo-link>
cd pet-inventory

# Install PHP dependencies
composer install

# Install JS dependencies
npm install && npm run dev
```

### 3. Database Setup (PostgreSQL)
1. Open your PostgreSQL terminal or a tool like pgAdmin.

2. Create a new database:
```bash
CREATE DATABASE pawradise_db;
```

3. Copy the environment file:
```bash
cp .env.example .env
```
4. Update your .env with your local credentials:
```bash
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=pawradise_db
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

### 4. Migrations & Storage
```bash
# Run database migrations
php artisan migrate

# IMPORTANT: Link the storage folder to make images accessible via web
php artisan storage:link

# Start the local development server
php artisan serve
```

## 🏗️ MVC Architecture & Structure

This project strictly follows the Model-View-Controller (MVC) pattern, supplemented by a Service Layer to maintain "Skinny Controllers" and "Fat Models/Services."
### Project Structure
```bash
pet-inventory/
├── app/
│   ├── Http/Controllers/
│   │   └── PetController.php      <-- [CONTROLLER] Brain of the app; handles requests and flow.
│   ├── Models/
│   │   └── Pet.php                <-- [MODEL] Database logic, fillables, and SoftDeletes.
│   └── Services/
│       └── PetImageService.php    <-- [SERVICE] Isolated logic for file uploads and deletions.
├── database/
│   └── migrations/                <-- [DATABASE] Defines the PostgreSQL table schema.
├── resources/
│   └── views/                     <-- [VIEW] The UI Layer
│       ├── layouts/               <-- Master Blade templates (Navigation, Global CSS).
│       ├── components/            <-- Reusable UI pieces (Pet Cards, Add-Pet Modals).
│       └── pets/                  <-- Specific page views (Index, Edit, Archive).
├── routes/
│   └── web.php                    <-- The "Route Map" defining all accessible URLs.
└── public/
    └── storage/                   <-- Symbolic link to access uploaded pet photos.
```
## 📸 Application Screenshots

Here is a visual overview of the Project Pawradise interface.

### Active Inventory (Dashboard)
This screen shows all currently active pets on campus. You can view their quick details, edit their profiles, or move them to the archive.

![Project Pawradise Dashboard View](img/Screenshot%202026-03-30%20224148.png)

### Archived Records
This view displays pets that have been soft-deleted. From here, records can be restored back to the active inventory or permanently removed from the system.

![Project Pawradise Archived View](img/Screenshot%202026-03-30%20224239.png)