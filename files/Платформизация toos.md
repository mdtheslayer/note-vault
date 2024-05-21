---
tags:
  - platform
  - toos
aliases: 
created: 2024-05-03, 14:50
modified: 2024-05-03, 14:50
updated: 2024-05-20T21:52
---

# Платформизация toos

- Resiliency(Восстановление/Устойчивость к сбоям)
	- Leader Election флинк
	- Геораспределенность (2-датацентра)
	- Archivability
		- Выгрузка в sdp
- Durability (Долговечность)
	- Fault tolerance
		- Восстановление процессов
		- Восстановление шагов
		- DLQ
		- TTL Entity Cassandra
- Configurability (Конфигурируемость)
	- Конфигурирование стратегий
		- Выбор доступных продуктов для сценария
			- Экспертно на основании бизнес-правил
			- На основании ML
		- Выбор приоритета/скорости стратегии
		- Выбор триггеров для старта сценария расчета
			- На основании source
			- Приоритизация триггеров между собой???
				- Актуально ли для рисковых триггеров? 
				- На основании веса триггера
				- На основании ML
		- Создание сценария расчета
			- External task node
			- Decision node
				- Praedicatum attributes
				- Global context
			- Source node
			- Parralell gateway node
			- Notification node
		- Подстановка variable под request
			- Map <String, Any>
	- Compatibility(Совместимость)
		- Проверка стратегий
		- Перенос стратегий между контурами
		- RBAC,ReBAC модель
		- Уведомления
			- time
			- email
	- Конфигурирование источников
		- Подключение топиков kafka
		- Подключение data source
		- Flink Table API & SQL
		- Контролирование потока по источнику
			- Включение/Выключение
			- Процент проходящего трафика
	- Конфигрурирование сплита в рамках теста
		- Statist
			- Просмотр аналитики
			- Конфигурирование количества выборки в рамках групп
- Maintainability
	- Тестирование стратегий
	- Тестирование конфигураций
		- Линтеры
		- Конструкторы ui
	- Появление metadata по офферу
		- ключ dco_general_id
- Observability
	- Alerts & Monitoring
		- SLI
			- Время выполнения процесса
			- Время выполнения шага
			- Количество протухших процессов
			- Количество технически ошибочных процессов
			- Количество технически ошибочных шагов
			- Все SLI Business Critical для процессов расчета
			- Все SLI Business Critical + для процессов удаления
		- SLA нижестоящих систем
			- PSAS
			- DED
			- DCO
			- COMMON-API
			- COMPLIANCE-API
			- SME-CREDIT-SCORING
			- COLD-SALES-MASTER
			- OFFER-STORAGE
	 - Maturity Model
		 - L1
		 - L2
		 - L3
- Stakeholders И/ИЛИ использующие систему
	- В людях
		- Product owner
		- Data analyst
		- Product analyst
		- Business analyst
		- Product manager
		- Solution architect
		- System analyst
	- Продукты
		- КН*
		- КК
		- POS
		- Некредитные продукты
		- Портфельные команды
	 - Каналы
		 - Magent
		 - TinkoffId
		 - Tsales
		 - Mobile
	- Бизнес-процессы
		- Экосистемное кредитование
		- X-SELL
- OKR
	- Увеличение линейки продуктов в TOOS
		- Зависимости 
			- Configurability 
			- Observability
			- Maintainability


---
# Back Matter
## Source
- [observability-maturity-model](https://516677.fs1.hubspotusercontent-na1.net/hubfs/516677/stackstate-observability-maturity-model.pdf)
- [NFRs](https://medium.com/bytebytego-system-design-alliance/top-10-architecture-characteristics-non-functional-requirements-with-cheatsheat-7ad14bbb0a9b)

## Tasks

- Определить наших потребителей. 
- Определить ценность по каждой функции

## Questions

- Какой стек для конфигурирования?
	- [Фиче флаги + их расширение через АБ Платформу](https://ded-dms.pages.devplatform.tcsbank.ru/dco-ui/docs/)  
	- [FTaaS от devplatform (на стадии дизайна)](https://wiki.tcsbank.ru/display/CORE/Feature+Toggles+as+a+service)  
	- [Resources от DED-DMS](https://wiki.tcsbank.ru/pages/viewpage.action?pageId=30533682)
	- [Headless CMS от DED-DMS](https://wiki.tcsbank.ru/pages/viewpage.action?pageId=1119123811)  
	- [Туллинг вокруг Gitlab + s3 + CDN](https://gitlab.tcsbank.ru/ded-dms/libs-resources-s3-runner-script)  
	- [Конфуций от RISKTECH](https://wiki.tcsbank.ru/pages/viewpage.action?pageId=2068176230)
	- Flink sql api
- Что нужно с технической точки зрения? Зайти к Вове, Коле
- Как определять ценность?

## Terms
<!-- Links to definition pages -->

## References
<!-- Links to pages not referenced in the content -->