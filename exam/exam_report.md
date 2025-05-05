University: ITMO University Faculty: FICT Course: Cloud platforms as the basis of technology entrepreneurship ADD link Year: 2025/2026 Group: OPOTPICT2-1 Author: Zaykina Aleksandra Exam: 8 case Date of create: 05.05.2025 Date of finished: 05.05.2025

## Проект: FoodEx Delivery — Автоматизация доставки еды
  
1. Цель проекта  
Создать масштабируемую систему для автоматической обработки заказов, прогнозирования времени доставки и адаптации к пиковым нагрузкам без необходимости содержания DevOps-команды.

2. Инструменты для продового решения  
Backend: FastAPI (микросервисы в Kubernetes)  
ML-инференс: TensorFlow Serving + GPU-кластер (NVIDIA T4)  
База данных: Yandex Managed ClickHouse (аналитика заказов)  
Оркестрация: Yandex Managed Kubernetes  
Мониторинг: Prometheus + Grafana + ELK-стек  
Кэш: Redis  
CI/CD: GitLab CI + ArgoCD  
  
3. Обоснование инструментов  
Kubernetes обеспечивает отказоустойчивость и автоскейлинг под нагрузку.  
ClickHouse быстро агрегирует данные тысяч заказов для аналитики.  
GPU-кластер ускоряет ML-модели (учет пробок, погоды).  
ELK-стек помогает оперативно выявлять ошибки в реальном времени.  
Бессерверные технологии (на MVP) минимизируют затраты на старте.  
  
4. Описание архитектуры  
Клиенты делают заказы через мобильное приложение или сайт.   
Запросы поступают в Kubernetes Ingress, который распределяет нагрузку между микросервисами.  
Backend на FastAPI обрабатывает заказы и обновляет их статусы в ClickHouse.  
Для прогнозирования времени доставки используется TensorFlow Serving на GPU.  
ML-модель учитывает исторические данные, пробки и погоду через внешние API.  
Redis кэширует частые запросы (например, статусы заказов).  
Prometheus собирает метрики с GPU и сервисов, Grafana визуализирует данные.  
Логи всех сервисов хранятся в ELK (Elasticsearch — поиск, Kibana — дашборды).  
GitLab CI и ArgoCD автоматически развертывают обновления.  
Система масштабируется при росте заказов (например, вечером или в выходные).  
  
5. Финансовые расчет затрат  
![2025-05-05_19-13-02](<img width="449" alt="exam" src="https://github.com/user-attachments/assets/ab0d6eef-b4a1-4e95-af31-1ec31c35bbe3" />
)  
  
6. Схема работы сервиса  
![lab4 - Frame 1](https://github.com/user-attachments/assets/a0ed12f3-cddc-4360-9358-88833e3f7382)  

