# AMI — Mobile Dating App

**AMI** — мобильное приложение для знакомств для Android, разработанное в рамках студенческого проекта.

Приложение позволяет пользователям создавать профиль, находить людей с похожими интересами, просматривать анкеты и общаться с другими пользователями.

## Features

* регистрация и авторизация пользователей;
* создание и редактирование профиля;
* просмотр профилей других пользователей;
* поиск и фильтрация пользователей;
* выбор интересов;
* выбор университета;
* просмотр информации о пользователе;
* система чатов;
* работа с данными пользователей через серверную часть;
* Android-приложение с нативным интерфейсом.

## Tech Stack

### Mobile

* **Kotlin / Java**
* **Android SDK**
* **Android Studio**
* **Gradle**

### Backend

* **PHP**
* REST-подобное взаимодействие мобильного приложения с сервером;
* серверные PHP-скрипты для регистрации, авторизации, поиска и получения данных.

### Database

* **MySQL**
* SQL-скрипты для создания и работы с базой данных.

## Architecture

Приложение построено по клиент-серверной архитектуре:

```text
┌──────────────────────────┐
│      Android App         │
│                          │
│  Profiles                │
│  Search & Filters        │
│  Interests               │
│  University              │
│  Chats                   │
└────────────┬─────────────┘
             │
             │ HTTP requests
             ▼
┌──────────────────────────┐
│       PHP Backend        │
│                          │
│  Authorization           │
│  Registration            │
│  Profile management      │
│  User filtering          │
│  Data retrieval          │
└────────────┬─────────────┘
             │
             │ SQL
             ▼
┌──────────────────────────┐
│        MySQL DB          │
│                          │
│  Users                   │
│  Profiles                │
│  Interests               │
│  Universities            │
│  Chats                   │
└──────────────────────────┘
```

## Project Structure

```text
AMI-MobileDatingApp/
│
├── app/
│   └── src/
│       └── main/
│           ├── java/
│           ├── res/
│           └── AndroidManifest.xml
│
├── gradle/
│   └── wrapper/
│
├── authorization.php       # User authorization
├── registration.php        # User registration
├── insertion_profile.php   # Profile data insertion
├── select_profile.php      # Profile retrieval
├── select_all_users.php    # User retrieval
├── filter_users.php        # User filtering
├── select_chat.php         # Chat data retrieval
├── select_interests.php    # Interests retrieval
├── select_univ.php         # Universities retrieval
│
├── ami.sql                 # Database structure and initial data
├── build.gradle
├── settings.gradle
├── gradle.properties
└── README.md
```

## Main User Flow

```text
Registration
     ↓
Create Profile
     ↓
Select Interests
     ↓
Select University
     ↓
Browse Users
     ↓
Filter Profiles
     ↓
View Profile
     ↓
Start Chat
```

## Database

The project includes `ami.sql` with the database structure required for the application.

The database stores information related to:

* users;
* user profiles;
* interests;
* universities;
* communication between users.

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/zitaisan/AMI-MobileDatingApp.git
cd AMI-MobileDatingApp
```

### 2. Open the project

Open the project in **Android Studio** and allow Gradle to download the required dependencies.

### 3. Configure the backend

Deploy the PHP files to a server with PHP and MySQL support.

Update the connection settings in the PHP files according to your local database configuration.

### 4. Create the database

Create a MySQL database and import:

```text
ami.sql
```

For example:

```bash
mysql -u username -p database_name < ami.sql
```

### 5. Configure the Android application

Update the backend/server URL in the Android application so that HTTP requests are sent to the deployed PHP backend.

### 6. Run the application

Run the project using Android Studio on:

* Android Emulator;
* physical Android device.

## Design

The application interface was designed in **Figma**.

[Figma Design](https://www.figma.com/design/03cMVQDrbP7A8nXQMlYcUu/Ami?node-id=547-132&t=a0GUZFZj7I5qySOs-1)

## Project Goals

The project was created to practice full-stack mobile application development and demonstrate the interaction between:

* Android client;
* backend API;
* relational database;
* user authentication;
* profile management;
* search and filtering;
* real-time-oriented communication scenarios.

## Future Improvements

Potential improvements include:

* implementing secure password hashing;
* replacing individual PHP endpoints with a structured REST API;
* adding JWT-based authentication;
* improving chat functionality with WebSocket;
* adding profile photos and media storage;
* implementing a recommendation/matching algorithm;
* adding likes and mutual matches;
* introducing notifications;
* migrating the backend to a modern framework;
* improving database normalization and indexing;
* adding automated tests.

## Author

**Taisia Zinchenko**

GitHub: [@zitaisan](https://github.com/zitaisan)

## Status

Student project / educational prototype.
