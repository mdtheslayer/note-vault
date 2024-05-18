---
tags:
  - platform
  - toos
aliases: 
created: 2024-05-03, 14:50
modified: 2024-05-03, 14:50
updated: 2024-05-18T16:19
---

# Платформизация toos

- Resiliency 
	- Leader Election флинк
	- Геораспределенность (2-датацентра)
	- Archivability
		- Выгрузка в sdp
- Durability
	- Fault tolerance
		- Восстановление процессов
		- Восстановление шагов
		- DLQ
		- TTL Entity Cassandra
- Configurability
	- Конфигурирование стратегий
		- Выбор доступных продуктов по сценарию
		- Выбор приоритета/скорости стратегии
		- Выбор сценария расчета
		- Создание сценария расчета
			- External task node
			- Decision node
				- Praedicatum attributes
				- Global context
			- Source node
			- Parralell gateway node
			- Notification node
	- Compatibility(Совместимость)
		- Проверка стратегий
		- Перенос стратегий между контурами
		- RBAC,ReBAC модель
		- Уведомления
			- time
			- email
- Maintainability
	- Тестирование стратегий
	- Тестирование конфигураций
		- Линтеры
		- Конструкторы ui
- Observability
	- Alerts & Monitoring
		- SLI
			- Время выполнения процесса
			- Время выполнения шага
			- Количество технически ошибочных процессов
			- Количество технически ошибочных по технике шагов
			- Все SLI Business Critical для процессов расчета
			- Все SLI Business Critical + для процессов удаления
	 - Maturity Model
		 - L1
		 - L2
		 - L3


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

## Terms
<!-- Links to definition pages -->

## References
<!-- Links to pages not referenced in the content -->