# Метод get
Возвращает указанный ресурс User для MongoDB.
 
Чтобы получить список доступных ресурсов User для MongoDB,
отправьте запрос [list](/docs/mdb/api-ref/mongodb/User/list).
 
## HTTP-запрос
`GET /managed-mongodb/v1/clusters/{clusterId}/users/{userName}`
 
## Path-параметры {#path_params}
 
Name | Description
--- | ---
clusterId | Обязательное поле. Идентификатор кластера MongoDB, к которому принадлежит пользователь. Чтобы получить идентификатор кластера, используйте запрос [list](/docs/mdb/api-ref/mongodb/Cluster/list).  Максимальная длина — 50 символов.
userName | Обязательное поле. Имя запрашиваемого ресурса User для MongoDB. Чтобы получить имя пользователя, используйте запрос [list](/docs/mdb/api-ref/mongodb/User/list).  Длина строки в символах должна быть от 1 до 63. Значение должно соответствовать регулярному выражению `` [a-zA-Z0-9_]+ ``.
 
## Ответ {#responses}
**HTTP Code: 200 - OK**

Ресурс User для MongoDB. Подробнее см. в разделе [Взаимосвязь ресурсов сервиса](/docs/mdb/concepts).
 
Поле | Описание
--- | ---
name | **string**<br><p>Имя пользователя MongoDB.</p> 
clusterId | **string**<br><p>Идентификатор кластера MongoDB, к которому принадлежит пользователь.</p> 
permissions | **object**<br><p>Набор разрешений, предоставленных пользователю.</p> 
permissions.<br>databaseName | **string**<br><p>Имя базы данных, к которой предоставляет доступ разрешение.</p> 
permissions.<br>roles | **string**<br><p>Роли MongoDB базы данных databaseName, которые предоставляет разрешение.</p> 