#  Схема
![alt text](/schema/schema.bmp)
## Описание
Возьмем ЦОД в вакууме, который предоставляет стойки для размещения своего железа, предоставляет в аренду физические сервера и виртуальные машины.
Необходимо хранить и агрегировать информацию о сделках с клиентами, получать информацию о затраченных ресурсов для выставления ежемесячных счетов. Счет может быть как статическим, так и динамическим по модели PAYG(pay as you go)
## Таблицы
### companies
Содержит необходимую информацию о компаниях.
### contacts
Содержит список сотрудников, которые представляют(а могут и нет) компанию.
### physycal_access
Сожержит информацию о посещении клиентами ЦОД для обслуживания своего сервера.
### employees
Список сотрудников ЦОД.
### tasks
Список задач, которые "висят" на сотруднике(например свзяться с клиентом по сделке).
### leads
Список сделок, как реализованных, так и в процессе заключения. В процессе движения сделки к заключению договора, для нее будут создаваться задачи на сотрудников.
### contracts
Список заключенных контрактов с компаниями.
### monthly_pays
Агрегирует в себе потребление серверов и виртуальных машин. Думаю, эта таблица заменится на noSQL решение, т.к. таблица хранит множество записей по каждой машине за определенный промежуток времени.

## Репликация и резервное копирование
Реплицировать БД на другую, физически независимую машину.
Резервное копирование выполнять по схеме 1 полное и 6 инрементальных. Полное в субботу ночью, инкрементальные каждую следующую ночь. Хранить полные бекапы за послелние пол года, инкрементальные за последний месяц.
