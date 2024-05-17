---
tags:
  - platform
  - toos
aliases:
  - Платформизация туза
  - туз
created: 2024-05-03, 18:45
modified: 2024-05-03, 18:45
updated: 2024-05-17T19:04
---

# Инсайды по конфигурации toos

1. Очень большая нагрузка, поэтому использовать синхронный вызов на процесс неверно.
   Опции:
	- push-модель. Мы где-то создаем конфигурацию и отправляем ее в сервис, который броадкастит по операторам в мемористейт
	- pull-модель. При старте приложения, необходимо для того чтобы восстановить предыдущий контекст.
2. Важно поддерживать версионирование
3. Важно иметь ролевую модель в формате rbac, rebac при возникновении конфликтов при заведении стратегий.
	- выявление конфликта
	- фиксация инцидента
	- уведомление time, почта 
		- узнать у Вовы по поводу Бота
4. Важно иметь возможность миграции с теста на прод конфигураций
5. Определить типы сущностей для конфигураций
	1. Кажется половину можно взять с бпмн.
6. Влияние процессов друг на друга
	1. Пакетные процесса
7. Анализ текущий бизесовых задач на предмет выноса логики
	1. Параметры канала и источников
	2. Какие продукты генерировать
	3. Какой тип сценария



---
# Back Matter
## Source
<!-- Always keep a link to the source. --> 
- 

## Tasks
<!-- What remains to be done with this note? --> 
- 

## Questions
<!-- What remains for you to consider? --> 
- 

## Terms
<!-- Links to definition pages -->
- 

## References
- [Фиче флаги + их расширение через АБ Платформу](https://ded-dms.pages.devplatform.tcsbank.ru/dco-ui/docs/)  
- [FTaaS от devplatform (на стадии дизайна)](https://wiki.tcsbank.ru/display/CORE/Feature+Toggles+as+a+service)  
- [Resources от DED-DMS](https://wiki.tcsbank.ru/pages/viewpage.action?pageId=30533682)
- [Headless CMS от DED-DMS](https://wiki.tcsbank.ru/pages/viewpage.action?pageId=1119123811)  
- [Туллинг вокруг Gitlab + s3 + CDN](https://gitlab.tcsbank.ru/ded-dms/libs-resources-s3-runner-script)  
- [Конфуций от RISKTECH](https://wiki.tcsbank.ru/pages/viewpage.action?pageId=2068176230)