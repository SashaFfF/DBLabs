# BDLabs
Филипеня Александра, гр. 153503. Предметная область - Афиша.
## Описание сущностей
### EventType
Таблица описывает типы мероприятий и содержит следующие поля:
- id - уникальный идентификатор; 
- type (char(50)) - тип мероприятия.
  
Связана с таблицей "Event" отношением "Один ко многим": мероприятие может быть только одного типа, но к одному типу может относится несколько мероприятий.
### Location
Таблица описывает место проведения мероприятия и содержит следующие поля:
- id - уникальный идентификатор; 
- city (char(50)) - город;
- street (char(50)) - улца;
- building_number (int) - номер здания;
- building_name (char(50)) - название здания.
  
Связана с таблицей "Event" отношением "Многие ко многим": одно мероприятие может проходить в нескольких местах, в то же время и в одном месте может проходить несколько мероприятий.
### Organizer
Таблица описывает организатора мероприятия и содержит следующие поля:
- id - уникальный идентификатор; 
- name (char(100)) - название организатора мероприятия;
- location_id (foreign key) - адрес организатора;
- phone_number (char(13)) - номер телефона.
  
Связана с таблицей "Event" отношением "Один ко многим": у одного мероприятия есть только один организатор, в то время как один органзатор может работать с несколькими мероприятиями.
Связана с таблицей "Location" отношением "Один к одному": один организатор располагается по одному адресу, то есть складывается отношение "один организатор - один адрес".
### AgeLimit
Таблица описывает возрастное ограничение на мероприятия и содержит следующие поля:
- id - уникальный идентификатор; 
- value (int) - значение возрастного ограничения.
  
Связана с таблицей "Event" отношением "Один ко многим": мероприятие имеет лишь одно значение возрастного ограничения, в то время как одинаковое значение возрастного ограничения может иметь несколько мероприятий.
### Event
Таблица описывает мероприятие и содержит следующие поля:
- id - уникальный идентификатор билета; 
- name (char(100)) - название мероприятия;  
- description (char(1000)) - описание мероприятия;  
- location_id (foreign key) - место проведения;  
- event_type_id (foreign key) - тип мероприятия;  
- date (datetime) - дата и время проведения мероприятия;  
- organizer_id (foreign key) - организатор;  
- age_limit_id (foreign key) - возрастное ограничение.

Связана с таблицей "EventType" отношением "Один ко многим": мероприятие может быть только одного типа, но к одному типу может относится несколько мероприятий.
Связана с таблицей "Location" отношением "Многие ко многим": одно мероприятие может проходить в нескольких местах, в то же время и в одном месте может проходить несколько мероприятий.
Связана с таблицей "Organizer" отношением "Один ко многим": у одного мероприятия есть только один организатор, в то время как один органзатор может работать с несколькими мероприятиями.
Связана с таблицей "AgeLimit" отношением "Один ко многим": мероприятие имеет лишь одно значение возрастного ограничения, в то время как одинаковое значение возрастного ограничения может иметь несколько мероприятий.
