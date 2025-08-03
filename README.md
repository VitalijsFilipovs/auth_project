# Django Auth Project

JWT-аутентификация с регистрацией, логином, обновлением токенов и выходом из аккаунта с использованием Django и DRF.

## 🔧 Стек технологий

- Python 3.13
- Django 5.2.4
- Django REST Framework
- Simple JWT
- SQLite

## ⚙️ Установка и запуск

bash
git clone https://github.com/VitalijsFilipovs/auth_project.git
cd auth_project
python -m venv .venv
.venv\Scripts\activate   # Windows
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver

------------------------------------------------

Регистрация пользователя
POST /api/register/
{
  "username": "vitaliy",
  "email": "vitaliy@example.com",
  "password": "StrongPass123!"
}

--------------------------------------------------

JWT логин
POST /api/login/
{
  "email": "vitaliy@example.com",
  "password": "StrongPass123!"
}


Ответ:

json
{
  "access": "eyJ...",
  "refresh": "eyJ..."
}

---------------------------------------------------

Обновление токена
POST /api/token/refresh/

json
{
  "refresh": "eyJ..."
}

-----------------------------------------------------

Logout (удаление refresh токена)
POST /api/logout/
Заголовок: Authorization: Bearer <access_token>

{
  "refresh": "eyJ..."
}
Ответ: 205 Reset Content
