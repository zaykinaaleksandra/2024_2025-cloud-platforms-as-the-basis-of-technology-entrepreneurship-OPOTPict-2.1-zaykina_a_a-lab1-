University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Cloud platforms as the basis of technology entrepreneurship](https://) ADD link  
Year: 2024/2025  
Group: OPOTP  
Author: Zaykina Aleksandra  
Lab: Lab4  
Date of create: 01.05.2025  
Date of finished: 02.05.2025

# Отчет по лабораторной работе №4

Разработка инфраструктуры MVP AI приложения

Цель работы:
Создать прототип AI-приложения с базовой функциональностью, разработать архитектуру для трех этапов (начальный, тестирование партнерами, прод), подобрать инструменты и рассчитать экономическую модель.

[Инфраструктура в Miro](https://miro.com/welcomeonboard/LzQrL3hrUTF1UVVhbWM2SEVjc200NVFBZE1JWG5RN2xqVWdwT1l5ZUJDaEdZRm5NVllrb2dTa0R0aExjT3g1Zk1vbHUxMmxZeHdzNHhZaTEwM0xJWDhWZ2xVclVSb1FOakVqRWovM0hJWHJGTmVwZUtDcjBYVFFoVnNIbnF5UTB0R2lncW1vRmFBVnlLcVJzTmdFdlNRPT0hdjE=?share_link_id=107140032850)

Этапы разработки инфраструктуры
## Этап 1: Начальный этап (MVP)
Архитектура:
Пользователи взаимодействуют с легковесным FastAPI-бекендом, развернутым в бессерверных контейнерах Yandex Cloud, где ML-модель работает через ONNX Runtime, а данные хранятся в Object Storage. Система автоматически масштабируется под нагрузку.

Инструменты:

Хранение данных: Yandex Object Storage

Backend: Python + FastAPI

ML-модель: ONNX Runtime

<img width="748" alt="1" src="https://github.com/user-attachments/assets/18f2bf8b-0e0a-4bb6-af15-41e4d7ad9b39" />

Финансовые расчеты:

Yandex Object Storage: 100 ГБ ~ $2/мес

Serverless Containers: 1M запросов ~ $0.5/мес

Итого: ~$2.5/мес

Обоснование:
Бессерверные технологии минимизируют затраты при старте, а ONNX Runtime обеспечивает достаточную производительность без GPU.

## Этап 2: Тестирование партнерами
Архитектура:
Приложение переносится на виртуальные машины с GPU-ускорением для Triton Inference Server, подключено к Managed PostgreSQL для надежного хранения данных, а Prometheus и Grafana обеспечивают мониторинг производительности.

Инструменты:

Хранение данных: Yandex Managed PostgreSQL

Backend: FastAPI на Yandex Compute

ML-модель: NVIDIA Triton Inference Server

Мониторинг: Prometheus + Grafana

CI/CD: GitLab Runner

<img width="580" alt="2" src="https://github.com/user-attachments/assets/a66f81e6-2133-4c8e-8f74-a28a11927009" />

Финансовые расчеты:

Compute VM: ~$20/мес

Managed PostgreSQL: ~$15/мес

GPU (NVIDIA T4): ~$200/мес

Итого: ~$235/мес

Обоснование:
GPU обеспечивают стабильную работу моделей при тестировании, а управляемая СУБД снижает эксплуатационные затраты.

## Этап 3: Продовое решение
Архитектура:
Масштабируемый кластер Kubernetes управляет микросервисами бекенда и TensorFlow Serving с GPU-кластером, данные хранятся в ClickHouse для аналитических нагрузок, а ELK-стек собирает логи и метрики для анализа.

Инструменты:

Хранение данных: Yandex Managed ClickHouse

Backend: Kubernetes

ML-модель: TensorFlow Serving + GPU-кластер

Мониторинг: ELK-стек

CI/CD: ArgoCD

<img width="617" alt="3" src="https://github.com/user-attachments/assets/687d04f1-6174-4883-a98b-cd68350a9b74" />

Финансовые расчеты:

Managed Kubernetes: ~$50/мес

ClickHouse: ~$100/мес

GPU Cluster: ~$600/мес

ELK: ~$30/мес

Итого: ~$780/мес

Обоснование:
Kubernetes обеспечивает отказоустойчивость, ClickHouse оптимизирован для аналитики, а GPU-кластер гарантирует высокую производительность ML-моделей.
