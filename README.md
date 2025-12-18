Контрольная работа №2
Студент Шевченко Л.Н. группа УИБО-02-24

Задание 1
Использованные данные:
Login: ' or 1=1;--               
Password: 321
Скриншот:

<img width="497" height="582" alt="Screenshot 2025-12-18 135852" src="https://github.com/user-attachments/assets/4a7eada9-41b9-487d-a701-bd8006e72ae1" />

Пользователь: 
Удалось войти как: admin@juice-sh.op
Скриншот:
<img width="334" height="286" alt="image" src="https://github.com/user-attachments/assets/c4fa2418-c6c4-4ef0-afe4-d1adf3218a9f" />

Почему удалось войти:
Удалось войти в админ‑аккаунт, потому что форма логина уязвима к SQL‑инъекции: введённая строка попала в SQL‑запрос без параметризации, изменила его логику на «условие всегда истинно» и часть проверки пароля фактически перестала учитываться.
Защита от SQL‑инъекций: использовать подготовленные выражения/параметризованные запросы (не склеивать SQL строками из пользовательского ввода) и дополнительно применять allow‑list валидацию входных данных.
SQL инъекция - злоумышленник внедряет вредоносный SQL-код в запросы приложения к базе данных через уязвимые поля ввода (формы, URL-параметры), чтобы обойти аутентификацию, получить доступ к конфиденциальным данным (пароли, карты), изменить, удалить информацию или получить полный контроль над системой
Задание 2
Email администратора:         
admin@juice-sh.op
Cookie: eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJzdGF0dXMiOiJzdWNjZXNzIiwiZGF0YSI6eyJpZCI6MSwidXNlcm5hbWUiOiJoaSIsImVtYWlsIjoiYWRtaW5AanVpY2Utc2gub3AiLCJwYXNzd29yZCI6IjAxOTIwMjNhN2JiZDczMjUwNTE2ZjA2OWRmMThiNTAwIiwicm9sZSI6ImFkbWluIiwiZGVsdXhlVG9rZW4iOiIiLCJsYXN0TG9naW5JcCI6IiIsInByb2ZpbGVJbWFnZSI6ImFzc2V0cy9wdWJsaWMvaW1hZ2VzL3VwbG9hZHMvZGVmYXVsdEFkbWluLnBuZyIsInRvdHBTZWNyZXQiOiIiLCJpc0FjdGl2ZSI6dHJ1ZSwiY3JlYXRlZEF0IjoiMjAyNS0xMi0xOCAxMDoxOToyNi45MTAgKzAwOjAwIiwidXBkYXRlZEF0IjoiMjAyNS0xMi0xOCAxMDozMzoyNi41NzcgKzAwOjAwIiwiZGVsZXRlZEF0IjpudWxsfSwiaWF0IjoxNzY2MDU2NTg5fQ.qS_USkSm0k8BGLX6KKddKkYT_RDM1jvSpGLqMhQXthYv_8vjxdiM9IewLKoXJl8v2PTnd4oTmlWG2OOSYcaVQFC_gU8BmZprl5ruTPm5lmExnX5Nuk1XladCn3QJxpH1Oa1aT3u0XOidGKGjFRuS4CMlaIb6e3jCwvX2aJjAdF0
Хэш пароля:           
0192023a7bbd73250516f069df18b500
Скриншотs:
<img width="906" height="756" alt="image" src="https://github.com/user-attachments/assets/7b3967cc-87b6-4546-a0fc-fc7132cfb221" />
<img width="612" height="616" alt="image" src="https://github.com/user-attachments/assets/e1490195-1322-46c9-bda7-08eb93aed003" />
<img width="785" height="66" alt="image" src="https://github.com/user-attachments/assets/9724a9e6-75de-4601-b7d0-5099422245e4" />

Метод получения пароля:             
Декодировал токен через base64decode.org    
Получил хэш пароля
Использовал crackstation.net для подбора
Результат: admin123

Что такое cookie            
Cookie — это данные, которые браузер хранит для поддержания сессии пользователя. В данном случае cookie содержит токен авторизации.
Как устранить уязвимость:
- не хранить пароли в токене
- не использовать предсказуемые токены (base64)
- использовать серверные сессии или JWT с подписью
- не хранить хэши пароля в cookies

Задание 3
Найденный параметр:         
bid (хранится в Session storage)
Скриншоты:
<img width="1297" height="725" alt="image" src="https://github.com/user-attachments/assets/cea435d9-83a4-47a8-93fc-34976eee5167" />
<img width="887" height="945" alt="image" src="https://github.com/user-attachments/assets/649b6fa0-9da4-4143-a58f-830764dea2b1" />
<img width="1027" height="515" alt="image" src="https://github.com/user-attachments/assets/9d307d2d-4823-4a07-a7ad-dfdf7a30f90b" />

Суть уязвимости:              
При изменении bid вручную, приложение показывает чужую корзину без проверки прав.
Этапы выполнения:
1. Добавил товары в корзину
2. Нашёл значение bid в Session storage
3. Изменил bid на другое значение
4. Обновил страницу
5. Получил доступ к чужой корзине
Как исправить:
- проверять владельца корзины на сервере
- не использовать изменяемые id в клиенте
- заменить ID на UUID + провести серверную проверку

Задание 4
Использованный script:
<img width="357" height="17" alt="image" src="https://github.com/user-attachments/assets/0896b5a3-b311-46f9-b28d-fb05ed3a0464" />

<a href="javascript:alert('XSS');">Click me</a>
Скриншот:
<img width="1919" height="161" alt="image" src="https://github.com/user-attachments/assets/60274a83-90c3-4410-a96a-0922d8687437" />
