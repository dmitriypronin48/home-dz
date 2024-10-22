# Домашнее задание  «Базы данных, их типы» - `Пронин Дмитрий Андреевич`

---

### Задание 1

Задание 1. СУБД
Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных. 
```
ответ: подойдет PostgreSQL , так как данная бд подойдет для больших объемов данных.
```
1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?
```
ответ: OpenSSl тут поддерживается многопоточность, что позволит использовать параллельные вычисления
```
1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.
```
ответ: как вариант MongoDB или тот же PostgreSQL, они же быстро масштабированые бд
```
1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?
```
ответ: можно, если использовать PostgreSQL , они по сути универсальная БД и вопросы должна закрыть все
```
1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.
```
ответ: если эта БД легковесная, то как вариант SQLite, если же более серьезная, то опять же PostgreSQL
```
1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?
```
ответ: да, можно, если проект строиться на PostgreSQL, то в целом с стороны архитектора проекта обычно описывается архитектура БД. То есть проектируются таблицы, делаются связи и индексы, и далее добавляются данные.
Ну и потом уже пишутся соответствующие запросы под бд. Аналитику можно даже вывести в Superset, так даже удобней. Там же и графики можно смотреть и таблички собирать.
```
1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.
```
ответ: можно использовать PostgreSQL, там есть функционал PostGis, он как раз может с геоданными работать.
```
1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?
```
ответ: Лучше сформировать мне кажется свою БД и сделать просто связи для обращения в другие бд. Если не ошибаюсь это может быть связано с dblink
```
1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?
```
ответ: да можно, через Postgresql
```



### Задание 2. Транзакции
2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.
инициализация транкзакции 
проверка наличия денежных средств
блокировка средств
обновление данных 
запись в журнал транкзакций 
подтверждение транкзакции
2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?
Планирование автоплатежа
Инициализация платежа по рассписанию
проверка наличия средств
блокировка средств
обновление данных 
запись в журнал транкзакций











