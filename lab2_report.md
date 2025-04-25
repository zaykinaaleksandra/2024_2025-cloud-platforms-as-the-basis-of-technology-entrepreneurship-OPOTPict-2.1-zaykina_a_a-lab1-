Зайдем в Cloud Run на Google Cloud Platform и нажмем на Deploy
<img width="1046" alt="1" src="https://github.com/user-attachments/assets/0b5a8981-104c-4fa3-8b74-6ac758b0de85" />
Используем существующий сервис hello и выставим минимальные настройки сервиса. Установим 8080 порт. Дадим доступ неавторизованным пользователям
<img width="537" alt="2" src="https://github.com/user-attachments/assets/3270dbc0-87cd-4048-a675-92a5b21e6d34" />
<img width="531" alt="3" src="https://github.com/user-attachments/assets/d476a282-70e5-4976-a79e-9030d52bc2fb" />
<img width="533" alt="4" src="https://github.com/user-attachments/assets/37212efb-02d7-48a7-84ea-29ba0f3075cf" />
Убедимся что сервис запущен
<img width="1043" alt="5" src="https://github.com/user-attachments/assets/89e17c69-5b04-4b20-9ae5-620703ecf752" />
По ссылке проверим работоспособность сервиса, удостоверяемся, что все сработало.
<img width="1043" alt="6" src="https://github.com/user-attachments/assets/61527535-787d-4839-845e-0b3bcec4a8df" />
Просмотрим текущие Logs и Metrics.
<img width="1046" alt="7" src="https://github.com/user-attachments/assets/36851665-71b5-44b2-95c4-530096ef094e" />
<img width="746" alt="8" src="https://github.com/user-attachments/assets/0cdd60fa-66ac-4475-bdba-c11a24bc69f6" />
Выставим для данного Cloud Run 8090 порт и применим трафик на 50%.
<img width="533" alt="9" src="https://github.com/user-attachments/assets/a3b6a6ac-8372-4068-9081-fe517eba233d" />
Рассмотрим изменения в метриках и при логах при изменении трафика и порта:
1.В логах видно, что контейнер теперь запускается и слушает порт 8090 вместо 8080.
2.Произошло обновление сервиса (ReplaceService), после чего контейнер выводит сообщение о старте на новом порту.
<img width="1041" alt="10" src="https://github.com/user-attachments/assets/fd86be62-bf4c-4bde-9173-bc3c9049c228" />
3.Container Instance Count: наблюдался всплеск до двух активных экземпляров во время переключения.
<img width="508" alt="14" src="https://github.com/user-attachments/assets/ef4e71b5-0023-495b-b233-5fac9ad8d23f" />
4.CPU/Memory Utilization: минимальные нагрузки, стабильные показатели (CPU около 1%, память около 10-20%).
<img width="1020" alt="15" src="https://github.com/user-attachments/assets/2b6a23f3-e410-4116-ba11-aefad4b44bee" />
5.Max Concurrent Requests: максимум 2 одновременных запроса во время переключения.
<img width="509" alt="16" src="https://github.com/user-attachments/assets/40b10569-d3a1-4133-8ee7-6ed77d926e2e" />
