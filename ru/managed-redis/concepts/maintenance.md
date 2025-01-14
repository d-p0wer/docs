# Техническое обслуживание

Под техническим обслуживанием понимается:

* автоматическая установка обновлений и исправлений СУБД для хостов (в т. ч. для выключенных кластеров);
* изменение класса хостов и объема хранилища;
* другие сервисные работы.

Порядок технического обслуживания кластеров {{ mrd-name }} определяется количеством хостов и наличием [шардов](sharding.md):

* В нешардированных кластерах из одного хоста техническое обслуживание проходит хост-мастер. Поэтому если во время технического обслуживания потребуется перезагрузка мастера, такой кластер станет недоступным.
* Если нешардированный кластер состоит из нескольких хостов, техническое обслуживание проводится в следующем порядке:

    1. [Хосты-реплики](replication.md) последовательно проходят техническое обслуживание. Порядок хостов в очереди определяется случайным образом. Если во время технического обслуживания потребуется перезагрузка реплики, она станет недоступной на это время.
    1. Хост-мастер проходит техническое обслуживание. Если во время технического обслуживания потребуется перезагрузка мастера и он станет недоступным, его роль возьмет на себя одна из реплик.

* В шардированных кластерах техническое обслуживание проходит пошардово в порядке возрастания номера шарда. Технического обслуживания хостов происходит так же как и в нешардированных кластерах.

Изменение версии СУБД не включено в техническое обслуживание. Подробнее о переходе между версиями см. в разделе [{#T}](../operations/cluster-version-update.md).
