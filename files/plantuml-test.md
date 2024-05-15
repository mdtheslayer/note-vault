```plantuml 
title Context diagram Tinkoff-Id in TOOS  
  
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml  
!include <cloudinsight/cassandra>  
!include <cloudinsight/kafka>  
!include <cloudinsight/postgresql>  
!include <cloudinsight/java>  
!include <cloudinsight/apache>  
!include <cloudinsight/redis>  
!include <cloudinsight/desktop>  
  
AddContainerTag("new container", $borderColor="Crimson", $bgColor="Crimson")  
AddContainerTag("changed container", $bgColor="Coral", $legendText="changed container")  
AddRelTag("new relation", $textColor="Crimson", $lineColor="Crimson", $lineStyle= BoldLine())  
AddRelTag("changed relation", $textColor="Coral", $lineColor="Coral", $lineStyle= BoldLine())  
  
Person(bank_client, "Personal Banking Customer", "Клиент банка тинькофф")  
Person(bank_operator, "Telephone Banking Operator", "Телефонные оператор банка")  
Person(bank_analyst, "Banking analyst", "Аналитик банка")  
  
Boundary(sales_tech, "Sales context"){  
    System(toos, "Toos", "Система генерации full-approve предложений", $sprite="apache")    
    System(hitman, "Hitman", "Система коммуникации с клиентом", $sprite="java")    
    System(sales_master, "Sales Master", "Система мастеринга продаж", $sprite="java")  
        
    Rel_R(toos, sales_master, "Команда расчета/окончания\nпродажи", "Kafka/Avro")        
    Rel(sales_master, hitman, "Команда расчета/окончания\nкоммуникации", "kafka/Avro")
}  
  
Boundary(marketing_context, "Marketing context"){  
    System_Ext(rtb, "rtb", "Система отображения контента на интерфейсах")    
    System_Ext(center_notification, "center notification", "Система по управлению активных коммуникаций")
}  
  
Boundary(client_process_context, "Client process context"){  
}  
  
  

Boundary(channel_context, "Toos Channel context"){  
    System_Ext(partners, "Partners", $sprite ="desktop", "Партнерские сервисы")    
    System_Ext(caen, "CAEN", "Выгрузка сегментов на скор")
    System_Ext(prime, "Prime", "Система для работы со счетами")
    System_Ext(tcrm, "tcrm", "CRM система")
    System_Ext(portfolio_platform, "portfolio-platform", "Система для работы с кредитным портфелем")
}  
  
Boundary(output_interface, "output-interface-context"){  
    System_Ext(mobile_app, "Mobile App", $sprite ="desktop", "Мобильное приложение")
    System_Ext(tele_sales, "Tsales", $sprite ="desktop", "Интерфейс для операторов")
}  
  
  
Boundary(command_context, "Toos Command Context"){  
    System_Ext(scoring, "scoring", "Система расчета условий")
    System_Ext(ded,"deduplication-evaluate", "Система работы с информацией по дублям")    
    System_Ext(dco, "dco", "Система по работе с a/b тестами и персонализацией контента")    
    System_Ext(cold_sales_master, "cold-sales-master", "Система мастеринга про")
}

Rel(partners, toos, "Клиентский триггер", "Rest/Json, Kafka/Avro")  
Rel(caen, toos, "Batch выгрузка", "Kafka/Avro")  
Rel(prime, toos, "Batch выгрузка", "Kafka/Json")  
Rel(tcrm, toos, "Batch выгрузка", "Kafka/Json")  
Rel(client_process_context, toos, "Триггеры по заявке", "Kafka/Json")  
Rel(portfolio_platform, toos, "Регламентные выгрузки")  
  
Rel(toos,scoring, "Скоринг офферов", "Kafka/Avro")  
Rel(toos,ded, "Обогащение данными по клиенту", "Rest/Json")  
Rel(toos,dco, "Обогащение персонализацией и тестами", "Rest/Json")  
  
Rel(hitman, rtb, "Создание коммуникации", "Kafka/Avro")  
Rel(hitman, center_notification, "Создание коммуникации", "Kafka/Avro")  
Rel(rtb,mobile_app, "Дай контент", "Rest/Json")  
Rel(center_notification,mobile_app, "Создание коммуникации")  
Rel(hitman,tele_sales, "Создание коммуникации", "Rest/Json")  
  
Rel(bank_analyst, caen, "Настройка скриптов для выгрузки")  
Rel(bank_client, mobile_app, "Посмотреть оффер, Клиентское действие")  
Rel(bank_client, partners, "Клиентское действие")  
Rel(bank_client, prime, "Работа со счетами")  
Rel(bank_client, tcrm, "Работа с перс данными")  
Rel_L(bank_operator, tele_sales, "Прозвон клиентов с целью предложения оффера")  
Rel(tele_sales, client_process_context,"")  
Rel(mobile_app, client_process_context,"")  
  
  
SHOW_LEGEND() 
```
