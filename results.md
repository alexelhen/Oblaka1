# Лабораторная работа №1  
**«Знакомство с IaaS, PaaS, SaaS сервисами в облаке на примере Amazon Web Services (AWS). Создание сервисной модели.»**  

**Вариант:** 10 

## Цель работы
Знакомство с облачными сервисами и уровнями абстракции над инфраструктурой в облаке (IaaS / PaaS / SaaS).  
Формирование понимания типов потребления сервисов в сервисной модели и подготовка данных для анализа затрат.

## Алгоритм работы
1. Взять входные данные от провайдера (AWS billing mapping rules).  
2. По **Product Code** определить сервис AWS.  
3. По **Usage Type** определить, *за что платим* (трафик, часы, запросы, сообщения и т.п.).  
4. Заполнить классификационные поля
5. Проверить логику по документации AWS.

## Теория
Облачные технологии — предоставление вычислительных ресурсов через интернет.  
Преимущества: гибкость, масштабируемость, доступность, оплата по факту использования.

Три основные модели облачных услуг:  
1. **IaaS** — инфраструктура как услуга;  
2. **PaaS** — платформа как услуга;  
3. **SaaS** — ПО как услуга.

В данной лабораторной работе основная цель — **правильно классифицировать потребляемые облачные ресурсы** (то, что приходит из биллинга).

### Что требуется в работе
Классифицировать потребляемые ресурсы по:  
1. Функциональной категории — **IT Tower** и **Service Family**;  
2. Сервису провайдера — **Service Type / Service Sub Type**;  
3. Типу потребления — **Service Usage Type** (за что берут деньги).

### Данные 
Использован файл: **Mapping Rules AWS team 10.csv**.  
Всего строк правил: **47**.

Логика заполнения:
- **Product Code** показывает сервис (например, AmazonS3, AmazonVPC);  
- **Usage Type** показывает паттерн тарификации (например, %DataTransfer%Bytes, %Requests-Tier1, %Storage).

## Результаты

###  Примеры заполнения 

| IT Tower | Service Family | Service Type | Service Sub Type | Service Usage Type | Product Code | Usage Type |
|---|---|---|---|---|---|---|
| Storage | Object Storage | Amazon S3 | Data Transfer | Data transfer (GB) | AmazonS3 | %DataTransfer% |
| Database | Ledger Database | Amazon QLDB | Storage | Storage (GB-months) | AmazonQLDB | %Storage |
| Analytics | Data Warehouse | Amazon Redshift | General | Usage-based | AmazonRedshift | nan |
| Network | Networking | Amazon VPC | General | Usage-based | AmazonVPC | nan |
| Cloud Services | Email | Amazon SES | General | Usage-based | AmazonSES | nan |
| Cloud Services | Messaging | Amazon SNS | General | Usage-based | AmazonSNS | nan |

## Заключение
Лабораторная работа №1 выполнена: данные AWS классифицированы по единой сервисной модели (IT Tower - Service Family - Service Type - Sub Type - Usage Type).  

