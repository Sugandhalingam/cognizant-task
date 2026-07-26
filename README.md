# 🎓 Cognizant Digital Nurture — Python Full Stack Engineering

[![Python](https://img.shields.io/badge/Python-3.12+-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-6.0-092E20?logo=django&logoColor=white)](https://www.djangoproject.com/)
[![Flask](https://img.shields.io/badge/Flask-3.x-000000?logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.140-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=black)](https://react.dev/)
[![Vue](https://img.shields.io/badge/Vue-3-4FC08D?logo=vue.js&logoColor=white)](https://vuejs.org/)
[![Angular](https://img.shields.io/badge/Angular-17-DD0031?logo=angular&logoColor=white)](https://angular.io/)
[![Selenium](https://img.shields.io/badge/Selenium-4.46-43B02A?logo=selenium&logoColor=white)](https://www.selenium.dev/)
[![MySQL](https://img.shields.io/badge/MySQL-8.x-4479A1?logo=mysql&logoColor=white)](https://www.mysql.com/)

> A complete, hands-on portfolio built for the **Cognizant Digital Nurture Program — Python Full Stack Engineering (Deepskilling) track**, covering backend frameworks, frontend frameworks, database integration, and automated testing with Selenium — all built around a single running theme: a **Student Course Management System**.

---

## 📌 About This Repository

This repository documents my progression through the Cognizant Digital Nurture training program. Every module is organized as a series of **hands-on exercises**, each one incrementally building the same core application — a Course/Student management platform — while introducing a new framework, tool, or concept.

Two things live side by side here:

| | Contains |
|---|---|
| **Task Briefs** | The original hands-on assignment PDFs given for each module (problem statements / requirements) |
| **Solutions** | My working implementation for every hands-on, organized module-by-module |

---

## 🗂️ Repository Structure

```
cognizant-task/
│
├── Module1_Python_Backend_Frameworks/
│   └── Sugandhalingam/
│       ├── hands_on_1  → hands_on_3   Django + Django REST Framework (models, serializers, APIs)
│       ├── hands_on_4  → hands_on_5   Flask + Flask-SQLAlchemy + Alembic migrations
│       ├── hands_on_6  → hands_on_9   FastAPI (schemas, validation, JWT auth & security)
│       └── hands_on_10                Microservices architecture (API Gateway pattern)
│
├── Module2_FrontendDevelopment/
│   └── Sugandhalingam/
│       ├── hands_on_1  → hands_on_2   Core HTML5 & CSS3 layouts
│       ├── hands_on_3  → hands_on_4   Vanilla JavaScript (DOM manipulation, dynamic rendering)
│       ├── hands_on_5  → hands_on_6   React (components, props, Redux Toolkit state)
│       ├── hands_on_7                 Angular (routing, components, services)
│       ├── hands_on_8  → hands_on_10  Vue 3 (Composition API, Pinia, Vue Router, Vite)
│       └── hands_on_9                 Polished static student portal (HTML/CSS/JS)
│
├── Module3_DatabaseIntegration/
│   └── Sugandhalingam/
│       ├── hands_on_1.sql → hands_on_3.sql   Schema design, joins, queries
│       ├── hands_on_4.py / .sql              MySQL performance: N+1 problem & optimization
│       ├── hands_on_5.js                     Node.js DB connectivity
│       ├── hands_on_6.pdf                    Transactions & indexing concepts
│       └── hands_on_7/                       SQLAlchemy ORM models + Alembic migrations
│
├── Module4_SeleniumBasics/
│   └── Sugandhalingam/
│       ├── hands_on_1 → hands_on_3    Selenium fundamentals & browser automation notes
│       ├── hands_on_4                 WebDriver setup & environment verification
│       ├── hands_on_5                 Locator strategies, explicit/implicit waits, XPath
│       ├── hands_on_6                 Pytest test suite + HTML reporting
│       └── hands_on_7                 Full Page Object Model (POM) framework
│
└── README.md
```

---

## 🧩 Module Breakdown

### 1️⃣ Python Backend Frameworks
Progressive implementation of the **same Course Management API** across three major Python frameworks, plus a microservices variant:

- **Django & DRF** — Models, serializers, ViewSets, admin panel, REST endpoints
- **Flask** — Blueprint-based structure, Flask-SQLAlchemy, Alembic schema migrations
- **FastAPI** — Pydantic schemas, dependency injection, OAuth2/JWT authentication, async endpoints
- **Microservices** — Independent `student_service` + `course_service`, unified behind an API Gateway

**Tech:** Python 3.12, Django 6.0, DRF, Flask, FastAPI, SQLAlchemy, Uvicorn, JWT (python-jose/passlib)

### 2️⃣ Frontend Development
The same **Student Portal UI** re-built across the frontend ecosystem to compare paradigms:

- Semantic HTML5 & modern CSS3 layouts
- Vanilla JavaScript DOM rendering with mock course data
- **React** — component composition + Redux Toolkit for enrollment state
- **Angular** — standalone components, routing, services
- **Vue 3** — Composition API, Pinia store, Vue Router, Vite build tooling

**Tech:** React 18, Angular 17, Vue 3, Vite, Pinia, Redux Toolkit, Axios

### 3️⃣ Database Integration
Relational database design and integration exercises against a **College/Course database**:

- Schema design, multi-table joins, and query writing (raw SQL)
- Identifying and fixing the classic **N+1 query problem** in Python (`mysql-connector-python`)
- Database connectivity from Node.js
- Transaction handling & indexing strategy
- **SQLAlchemy ORM models with Alembic version-controlled migrations**

**Tech:** MySQL, SQLAlchemy, Alembic, mysql-connector-python, Node.js

### 4️⃣ Selenium Basics (Test Automation)
A test automation track that builds up to a production-style framework:

- Selenium WebDriver fundamentals & environment setup
- Locator strategies (ID, CSS, XPath) and explicit/implicit wait strategies
- Test suites with **Pytest**, screenshot capture on failure, and HTML test reports
- A complete **Page Object Model (POM)** framework with reusable base page classes

**Tech:** Selenium 4.46, Pytest, pytest-html, webdriver-manager

---

## ⚙️ Getting Started

Each hands-on folder is a **self-contained project**. General setup pattern:

### Python-based hands-ons (Django / Flask / FastAPI / Selenium)
```bash
cd <hands_on_folder>
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

**Django**
```bash
python manage.py migrate
python manage.py runserver
```

**Flask**
```bash
flask db upgrade      # where migrations are present
python app.py
```

**FastAPI**
```bash
uvicorn main:app --reload
```
Docs available at: `http://localhost:8000/docs`

**Selenium test suites**
```bash
pytest --html=report.html
```

### Frontend hands-ons (React / Vue / Angular)
```bash
cd <hands_on_folder>
npm install
npm run dev        # Vue/Vite
npm start          # React/Angular
```

### Static HTML/CSS/JS hands-ons
Simply open `index.html` in a browser — no build step required.

---

## 🛠️ Tech Stack Summary

| Layer | Technologies |
|---|---|
| **Backend** | Python, Django, Django REST Framework, Flask, FastAPI, Uvicorn |
| **Frontend** | HTML5, CSS3, JavaScript (ES6+), React, Redux Toolkit, Vue 3, Pinia, Angular |
| **Database** | MySQL, SQLAlchemy ORM, Alembic |
| **Testing/QA** | Selenium WebDriver, Pytest, Page Object Model |
| **Tooling** | Vite, npm, pip, Git |

---

## 👤 Author

**Sugandhalingam**
Cognizant Digital Nurture — Python Full Stack Engineering (Deepskilling)

---

## 📄 License

This repository contains personal learning exercises completed as part of a corporate training program and is shared for portfolio/reference purposes.
