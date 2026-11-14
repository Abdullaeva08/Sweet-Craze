# 🍰 Sweet-Craze

Таттуу азыктарды жана десерттерди заказ кылуу үчүн онлайн дүкөн — Django жана DRF менен.

---

## 💡 Идея

**Sweet-Craze** — торттор, пирожныйлар, момпосуйлар жана башка таттуулар сатылуучу онлайн дүкөн.
Кардар каталогдон өзүнө жаккан таттуулукту тандап, себетке салып, заказ берет жана анын абалын көрүп турат.

Долбоордун негизги максаты — **чыныгы backend архитектурасын** үйрөнүү: моделдер, авторизация, себет жана заказ логикасы.

---

## 🎯 Негизги функциялар

| 👤 Кардар | 🛠️ Администратор |
|---|---|
| Каттоо жана кирүү | Азыктарды кошуу / түзөтүү / өчүрүү |
| Каталогду көрүү | Категорияларды башкаруу |
| Издөө жана фильтрлөө | Заказдарды кабыл алуу |
| Себетке кошуу | Заказдын статусун өзгөртүү |
| Заказ берүү | Баа жана сүрөт коюу |
| Заказдардын тарыхы | Django admin панели |
| Тандалмаларга кошуу | |
| Сын-пикир калтыруу | |

> ⚠️ Коддо жок функцияларды таблицадан өчүрүп салыңыз.

---

## 🗃️ Маалымат модели

```
User ──┬── Cart ── CartItem ── Product
       │
       ├── Order ── OrderItem ── Product
       │       └── status: new → preparing → delivering → done
       │
       └── Review ── Product

Category ── Product
```

| Модель | Милдети |
|---|---|
| `User` | Колдонуучу жана анын ролу |
| `Category` | Категория (торттор, пирожныйлар, момпосуйлар) |
| `Product` | Азык: аталышы, баасы, сүрөтү, сүрөттөмөсү |
| `Cart`, `CartItem` | Кардардын себети |
| `Order`, `OrderItem` | Заказ жана анын курамы |
| `Review` | Сын-пикир жана рейтинг |

---

## ⚙️ Орнотуу

```bash
git clone https://github.com/<username>/sweet-craze.git
cd sweet-craze

python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

📍 `http://127.0.0.1:8000/`

**`.env` мисалы:**

```env
SECRET_KEY=your-secret-key
DEBUG=True
DB_NAME=sweet_craze
DB_USER=postgres
DB_PASSWORD=password
```

---

## 🔌 API эндпоинттер

<details>
<summary><b>🔐 Авторизация</b></summary>

| Метод | URL | Сүрөттөмө |
|---|---|---|
| POST | `/api/auth/register/` | Каттоо |
| POST | `/api/auth/login/` | Кирүү |

</details>

<details>
<summary><b>🧁 Каталог</b></summary>

| Метод | URL | Сүрөттөмө |
|---|---|---|
| GET | `/api/categories/` | Категориялар |
| GET | `/api/products/` | Азыктардын тизмеси (издөө, фильтр) |
| GET | `/api/products/<id>/` | Азыктын чоо-жайы |
| POST | `/api/products/` | Азык кошуу (админ) |

</details>

<details>
<summary><b>🛒 Себет жана заказдар</b></summary>

| Метод | URL | Сүрөттөмө |
|---|---|---|
| POST | `/api/cart/` | Себетке кошуу |
| DELETE | `/api/cart/<id>/` | Себеттен өчүрүү |
| POST | `/api/orders/` | Заказ берүү |
| GET | `/api/orders/my/` | Менин заказдарым |
| PATCH | `/api/orders/<id>/status/` | Статусту өзгөртүү (админ) |

</details>

> URL'дерди өз долбооруңуздагыга жараша өзгөртүңүз.

---

## 🗺️ План

- [x] Авторизация
- [x] Каталог жана категориялар
- [x] Себет жана заказдар
- [ ] Төлөм системасын кошуу
- [ ] Email / Telegram билдирмелери
- [ ] Docker менен ишке киргизүү
- [ ] Тесттерди жазуу

> Чекбокстарды өз прогрессиңизге жараша өзгөртүңүз.

---

## 👩‍💻 Автор

**Abdullaeva Fatima**
Junior Backend Developer · Python · Django · DRF

[GitHub](https://github.com/<username>)
