## Ссылка на коллекцию:
тут
## Создание пользователя
> Метод и ручка: POST/api/v1/users

```
{
			"name": "Создание пользователя",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"firstName\": \"Анатолий\",\r\n    \"phone\": \"+79995553322\",\r\n    \"address\": \"г. Москва, ул. Пушкина, д. 10\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/users",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"users"
					]
				}
			},
			"response": []
		}

```

## Получить список складов
> Метод и ручка: GET/api/v1/warehouses

```
{
			"name": "Получить список складов",
			"protocolProfileBehavior": {
				"disableBodyPruning": true
			},
			"request": {
				"method": "GET",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/warehouses",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"warehouses"
					]
				}
			},
			"response": []
		}

```

## Создание набора
> Метод и ручка: POST/api/v1/kits?cardId=1

```
{
			"name": "Создание набора",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"cardId\": 1, \r\n    \"name\": \"Мой набор\" \r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/kits?cardId=1",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"kits"
					],
					"query": [
						{
							"key": "cardId",
							"value": "1"
						}
					]
				}
			},
			"response": []
		}
```

## Получение всех наборов
> Метод и ручка: GET/api/v1/kits?cardId=1

```
{
			"name": "Получение всех наборов",
			"protocolProfileBehavior": {
				"disableBodyPruning": true
			},
			"request": {
				"method": "GET",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/kits?cardId=1",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"kits"
					],
					"query": [
						{
							"key": "cardId",
							"value": "1"
						}
					]
				}
			},
			"response": []
		}
```

## Добавление продуктов в набор
> Метод и ручка: POST/api/v1/kits/id/products

```
{
			"name": "Добавление продуктов в набор",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"productsList\": [\r\n        {\r\n            \"id\": 1,\r\n            \"quantity\": 2\r\n        },\r\n        {\r\n            \"id\": 6,\r\n            \"quantity\": 2\r\n        }\r\n    ]\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/kits/7/products",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"kits",
						"7",
						"products"
					]
				}
			},
			"response": []
		}
```

## Удаление набора
> Метод и ручка: DELETE/api/v1/kits/id

```
{
			"name": "Удаление набора",
			"request": {
				"method": "DELETE",
				"header": [],
				"url": {
					"raw": "{{server_url}}/api/v1/kits/7",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"kits",
						"7"
					]
				}
			},
			"response": []
		}
```

## Создание корзины
> Метод и ручка:POST/api/v1/orders

```
{
			"name": "Создание корзины",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"productsList\": [\r\n        {\r\n            \"id\": 1,\r\n            \"quantity\": 2\r\n        },\r\n        {\r\n            \"id\": 5,\r\n            \"quantity\": 2\r\n        },\r\n        {\r\n            \"id\": 3,\r\n            \"quantity\": 1\r\n        }\r\n    ]\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/orders",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"orders"
					]
				}
			},
			"response": []
		}
```

## Добавление товаров в корзину
> Метод и ручка:PUT/api/v1/orders/id

```
{
			"name": "Добавление товаров в корзину",
			"request": {
				"method": "PUT",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"productsList\": [\r\n        {\r\n            \"id\": 1,\r\n            \"quantity\": 1\r\n        },\r\n        {\r\n            \"id\": 5,\r\n            \"quantity\": 1\r\n        },\r\n        {\r\n            \"id\": 3,\r\n            \"quantity\": 1\r\n        },\r\n        {\r\n            \"id\": 4,\r\n            \"quantity\": 1\r\n        }\r\n    ]\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/orders/2",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"orders",
						"2"
					]
				}
			},
			"response": []
		}
```

## Получение продуктов в корзине
> Метод и ручка:GET/api/v1/orders/id

```
{
			"name": "Получение продуктов в корзине",
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{server_url}}/api/v1/orders/2",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"orders",
						"2"
					]
				}
			},
			"response": []
		}
```

## Получить список доставок
> Метод и ручка:GET/api/v1/couriers

```
{
			"name": "Получить список доставок",
			"request": {
				"method": "GET",
				"header": [],
				"url": {
					"raw": "{{server_url}}/api/v1/couriers",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"couriers"
					]
				}
			},
			"response": []
		}
```

## Проверить стоимость доставки
> Метод и ручка:POST/api/v1/couriers/check

```
{
			"name": "Проверить стоимость доставки",
			"request": {
				"method": "POST",
				"header": [],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"products\": [\r\n        {\r\n            \"id\": 1,\r\n            \"quantity\": 3\r\n        },\r\n        {\r\n            \"id\": 4,\r\n            \"quantity\": 1\r\n        },\r\n        {\r\n            \"id\": 9,\r\n            \"quantity\": 3\r\n        }\r\n    ],\r\n    \"deliveryTime\": 7\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{server_url}}/api/v1/couriers/check",
					"host": [
						"{{server_url}}"
					],
					"path": [
						"api",
						"v1",
						"couriers",
						"check"
					]
				}
			},
			"response": []
		}
```
