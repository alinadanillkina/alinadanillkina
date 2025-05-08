University: ITMO University  
Faculty: FTMI  
Course: Cloud platforms as the basis of technology entrepreneurship  
Year: 2024/2025  
Group: UVB  
Author: Danilova Alina  
Lab: Lab1  
Date of create: 26.04.2025  
Date of finished: 26.04.2025  


Зашли в вкладку IAM, создали service account. Выбрана роль администратора хранилища
<img width="1130" alt="Снимок экрана 2025-05-08 в 21 45 51" src="https://github.com/user-attachments/assets/8427c047-4ed5-428b-9db3-e83a65f9e0d4" />

Открыт раздел Compute Engine, создала минимальный compute engine (виртуальную машину) с Machine type e2-micro в режиме spot.
<img width="1426" alt="image" src="https://github.com/user-attachments/assets/0c2d697b-9708-4412-b9f0-498f05a1a5c3" />


Выполнено подключение к созданной виртуальной машине через SSH. В окне подключения выполнены команды для создания новой папки и копирования в неё необходимых файлов. После выполнения операций SSH-сессия завершена.
![telegram-cloud-photo-size-2-5235721844751986805-y](https://github.com/user-attachments/assets/1773979f-1178-48e1-a793-116e4c6a499d)

Поменяла права доступа для вашего service account с Storage Admin на Compute Viewer. Далее произвела повторное подключение к виртуальной машине через SSH. При попытке переноса данных возникла ошибка, указывающая на недостаточность прав доступа  
<img width="932" alt="Снимок экрана 2025-05-08 в 22 07 27" src="https://github.com/user-attachments/assets/09e45904-fd02-4f8e-a915-c3665e52dcd8" />
![Group 1](https://github.com/user-attachments/assets/b89ed60b-30b1-4036-8257-1b4377eeab45)




Виртуальная машина и сервисный аккаунт удалены.



