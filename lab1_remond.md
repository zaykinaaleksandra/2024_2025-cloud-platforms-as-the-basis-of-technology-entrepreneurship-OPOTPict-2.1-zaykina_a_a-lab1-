University: ITMO University Faculty: FICT Course: Cloud platforms as the basis of technology entrepreneurship ADD link Year: 2025/2026 Group: OPOTPICT2-1 Author: Zaykina Aleksandra Lab: Lab1 Date of create: 22.04.2025 Date of finished: 22.04.2025
Зашли в вкладку IAM, создали service account с ролью Storage Admin
<img width="1042" alt="lab (0)" src="https://github.com/user-attachments/assets/872304db-0a89-4eb0-aefe-66266ac24981" />
Создали минимальный compute engine (виртуальную машину) с Machine type e2-micro в режиме spot.
<img width="1040" alt="lab (5)" src="https://github.com/user-attachments/assets/e7c288bd-dc45-469d-a2d7-9eccc343b52e" />
С помощью утилиты gsutils нашли бакет lab1-bucket-itmo и скопировали 3 файла в локальную папку на VM. Используя команду ls -lah отобразили, что эти файлы хранятся у нас на VM.
<img width="660" alt="lab 1 (1)" src="https://github.com/user-attachments/assets/b6840e2a-01e8-48f3-a2e6-9bd375bd2d76" />
Поменяли права доступа для нашего service account с Storage Admin на Compute Viewer, попробовали повторить пункт с копированием данных, сделали выводы - нет возможности подключиться к VM.
<img width="1043" alt="lab (4)" src="https://github.com/user-attachments/assets/9d7fb1fd-2ee9-43c1-a728-80a2c25f8682" />
<img width="658" alt="lab 1 (2)" src="https://github.com/user-attachments/assets/8ddc1815-229b-49c6-bdbb-9d67b0503408" />
