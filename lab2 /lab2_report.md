University: ITMO University  
Faculty: FTMI  
Course: Cloud platforms as the basis of technology entrepreneurship  
Year: 2024/2025  
Group: UVB  
Author: Danilova Alina  
Lab: Lab2  
Date of create: 5.05.2025  
Date of finished: 8.05.2025  


Заходим в Cloud Run на Google Cloud Platform и нажмем на Deploy.  
Используем существующий сервис hello (us-docker.pkg.dev/cloudrun/container/hello) и выставим минимальные настройки сервиса.   
Установим 8080 порт.  
<img width="1439" alt="image" src="https://github.com/user-attachments/assets/f023ce33-5550-4286-bc68-1ac087b06e26" />
Проверим, что сервис запускается  
<img width="1069" alt="image" src="https://github.com/user-attachments/assets/c399dc55-2b19-4b08-b4b8-9aef63ba4edd" />
  
Смотрим что в текущих логах  
![Group 2](https://github.com/user-attachments/assets/d74a604c-9092-4ecd-9210-a7144d45ca30)
  
Изменим порт на 8090. Сервер успено запустился 
<img width="1185" alt="image" src="https://github.com/user-attachments/assets/f08bdfb8-362f-4b33-8742-991a5a7b7eb1" />  
  
<img width="1047" alt="Снимок экрана 2025-05-08 в 23 35 09" src="https://github.com/user-attachments/assets/72c5d71f-eafb-4506-a20a-0612f4c9f003" />  
<img width="1409" alt="Снимок экрана 2025-05-08 в 23 40 48" src="https://github.com/user-attachments/assets/3810cfc2-92c6-49bb-b670-0be2af1dd691" />

 
**Выводы**  
- ReplaceService - Обновление сервиса
- Далее в логах отражено, что контейнер теперь запускается и слушает порт 8090 вместо 8080. сообщение о старте на новом порту.
- по метрикам: увеличение Container Instance Count до 2 во время переключения портов
  
сервисы удалены

