University: ITMO University  
Faculty: FTMI  
Course: Cloud platforms as the basis of technology entrepreneurship  
Year: 2024/2025  
Group: UVB  
Author: Danilova Alina  
Lab: Lab2  
Date of create: 11.05.2025  
Date of finished: 11.05.2025  
  

Лабораторная работа №4 "Разработка инфраструктуры MVP AI приложения."
Цель работы: Создать прототип AI-приложения с базовой функциональностью.  

https://miro.com/app/board/uXjVI3RekpI=/?share_link_id=433534843895

## Инфраструктура Telegram-бота, который генерит подборку фильмов по запросу пользователя

## Этап 1: MVP (до 30 пользователей в неделю)  
Цель: Быстро развернуть базовую версию бота для проверки идеи.  
<img width="793" alt="image" src="https://github.com/user-attachments/assets/50055acb-c9f6-4c4b-a2b3-9432708d990a" />


| Компонент             | Инструмент                     | Обоснование |
|-----------------------|----------------------------------|-------------|
| Обработка запросов    | Cloud Functions (Python)        | Бесплатно до 2 млн вызовов, просто и быстро |
| Telegram              | Telegram Bot API                | Готовые методы |
| Фильмы                | TMDb API                        | Бесплатный план |

**Примерная стоимость:** $0–5/мес

---

## Этап 2: Тестирование с партнёрами (до 150 пользователей)  
Цель: Увеличить масштабы системы для тестирования на большем числе пользователей.  
<img width="876" alt="image" src="https://github.com/user-attachments/assets/9fab126d-765f-4f27-8536-7e2ebb6a1fcb" />
  
Как всё работает:  
	1.	Пользователь отправляет запрос → он проходит через Telegram Bot API.  
	2.	Вместо функции теперь используется Cloud Run — это как мини-приложение в облаке, которое запускается при запросе.  
	3.	Cloud Run:  
	•	Сначала проверяет, нет ли уже подходящего ответа в Cloud Storage (это как облачный “жёсткий диск”).  
	•	Если кеша нет — делает запрос в TMDb API.  
	•	Сохраняет результат в Cloud Storage, чтобы в следующий раз не искать заново.  
	4.	Запрос, тема и ответ сохраняются в Firestore — облачная база данных.  
	5.	Всё логируется через Cloud Logging — можно потом посмотреть статистику и ошибки.  
	6.	Ответ возвращается в Telegram.  
| Компонент               | Инструмент                       | Обоснование |
|-------------------------|----------------------------------|-------------|
| Обработка запросов      | Cloud Run                        | Устойчивый запуск кода в Docker |
| Хранение запросов       | Firestore                        | NoSQL база от Google |
| Кеширование             | Cloud Storage (Standard)         | Быстрое хранение изображений и json |
| Логи и мониторинг       | Cloud Logging                    | Анализ ошибок и логов |

**Примерная стоимость:** $10–15/мес

---

## Этап 3: Продакшн (около 1000 пользователей)  
Цель: Оптимизация и масштабируемость для работы с массовой аудиторией.  
<img width="765" alt="image" src="https://github.com/user-attachments/assets/223e79ce-9147-4f3c-8ae4-3c5d72779a3f" />
Как всё работает:  
	1.	Пользователь пишет в Telegram → Telegram Bot API передаёт сообщение.  
	2.	Cloud Run принимает запрос. Если нагрузка большая, используется GKE (система для распределения нагрузки).  
	3.	Программа может:  
	•	Понять смысл запроса с помощью OpenAI API или Vertex AI (например, “подбери триллеры с сюжетом про месть”).  
	•	Обратиться к BigQuery — системе для хранения и анализа больших объёмов данных.  
	•	Получить список фильмов через TMDb API.  
	4.	Хранит все результаты и изображения в Cloud Storage.  
	5.	Всё, что происходит, логируется в Cloud Logging.  
	6.	Ответ уходит обратно пользователю через Telegram.  

| Компонент               | Инструмент                          | Обоснование |
|-------------------------|-------------------------------------|-------------|
| Обработка запросов      | Cloud Run                           | Простое масштабирование |
| Искусственный интеллект | Vertex AI                           | Гибкость и настройка ИИ |
| Хранение и аналитика    | BigQuery                            | Для анализа больших объёмов |
| Хранение файлов         | Cloud Storage                       | Быстрый доступ к медиафайлам |
| Балансировка нагрузки   | Cloud Load Balancer + VPC           | Надёжность и масштаб |

**Примерная стоимость:** $60–80/мес  
  
## 💸 Стоимость инструментов на каждом этапе

| Инструмент | MVP (до 30 пользователей) | Тестирование (до 150 пользователей) | Продакшн (1000 пользователей) |
|------------|-----------------------------|--------------------------------------|-------------------------------|
| Cloud Functions | $0 | $- | $- |
| TMDb API | $0 | $0 | $0 |
| Telegram Bot API | $0 | $0 | $0 |
| Cloud Run | $- | $10 | $30 |
| Firestore | $- | $1 | $5 |
| Cloud Storage | $- | $1 | $5 |
| Cloud Logging | $- | $0 | $2 |
| Vertex AI | $- | $- | $20 |
| BigQuery | $- | $- | $10 |
| Cloud Load Balancer | $- | $- | $5 |
| ИТОГО | $0 | $12 | $77 |**
  


