# Let's Gas API Documentations

Version: 19082019.1

### Contents ( Based on Activities )

1. Gas Stations
   - get all nearest gas stations
   - get gas stations by id
2. Orders
   - Histories
   - Get order details ( fetch admin cost, and base product prices )
   - Post order
   - Barcode scans / Order scans
3. Bundles ( packets )
   - Get all bundles
4. Profiles
   - get fake link aja balances
   - get user subscriptions
   - login
   - logout



## 1. Gas Stations

Base URL: /gas-stations/

#### Get All Nearest Gas Stations

##### Request

Url:

- /gas-stations/nearest/

Method:

- GET

Params:

- lat: float value of latitude
- lng: float value of longitude

##### Response

```json
{
    "next": "/gas-stations/nearest/?lat=-6.23301&lng=121.18123&page=2",
    "prev": null,
    "total_page": 2,
    "total_item": 11,
    "data": [
        {
            "id": 1,
            "address": "Jalan Limo Kebayoran Lama, Grogol Utara, Jakarta Selatan, 12220",
            "photo_url": "https://somebucket.com/ae231cb.png",
            "lat": -6.241,
            "lng": 121.19238189,
            "distance": "1.5",
            "open_at": "08:00",
            "closed_at": "21:00",
            "is_open": true,
            "name": "31.143.01",
            "facilities": [
                {
                    "id": 33,
                    "gas_station_id": 1,
                    "name": "Toilet",
                    "icon": "https://somebucket.com/ce811fe.png",
                    "is_available": true,
                },
            ],
            "products": [
                {
                    "id": 120,
                    "gas_station_id": 1,
                    "name": "premium",
                },
            ],
            "visitors": {
                "id": 1232,
                "gas_station_id": 1,
                "count": 12,
                "is_full": false,
                "wait_duration_minutes": 15.23333,
                "updated_at": "2019-08-19 09:31:11",
            }
        },
    ],
}
```



#### Get Gas Station by Id

##### Request

Url:

- /gas-stations/by-id/{gas_station_id}

Method:

- GET

Params:

- none

##### Response

```json
{
    "data": {
        "id": 1,
        "address": "Jalan Limo Kebayoran Lama, Grogol Utara, Jakarta Selatan, 12220",
        "photo_url": "https://somebucket.com/ae231cb.png",
        "lat": -6.241,
        "lng": 121.19238189,
        "distance": "1.5",
        "open_at": "08:00",
        "closed_at": "21:00",
        "is_open": true,
        "name": "31.143.01",
        "facilities": [
            {
                "id": 33,
                "gas_station_id": 1,
                "name": "Toilet",
                "icon": "https://somebucket.com/ce811fe.png",
                "is_available": true,
            },
        ],
        "products": [
            {
                "id": 120,
                "gas_station_id": 1,
                "name": "premium",
            },
        ],
        "visitors": {
            "id": 1232,
            "gas_station_id": 1,
            "count": 12,
            "is_full": false,
            "wait_duration_minutes": 15.23333,
            "updated_at": "2019-08-19 09:31:11",
        },
    },
}
```

## 2. Orders

Base URL: /orders/

#### Histories

##### Request

Url:

- /orders/histories/

Method:

- GET

Params:

- none

##### Response

```json
{
    "next": "/orders/histories/&page=1",
    "prev": null,
    "total_page": 2,
    "total_item": 11,
    "data": [
    	{
            "id": 1,
            "type": "SUBSCRIPTION",
            "code": "#SB340LM1",
            "total": 223000,
            "admin_fee": 3000,
            "subscriptions": {
                "id": 1,
                "name": "Subscription Pertralite 30L",
                "quantity": 30.0,
                "duration_in_days": 30,
                "price": 220000,
            },
            "product": {
                "id": 2,
                "name": "pertralite",
            },
            "gas_station": {
                "id": 1,
                "name": "31.143.01",
            },
            "created_at": "2019-08-19 11:02:22",
        },
        {
            "id": 2,
            "type": "PETROL",
            "code": "#PS340LM1",
            "subscriptions": null,
            "product": {
                "id": 2,
                "name": "pertralite",
                "price": 7680,
            },
            "quantity": 3.13,
            "gas_station": {
                "id": 1,
                "name": "31.143.01",
            },
            "created_at": "2019-08-19 11:02:22",
        },
    ],
}
```

#### Get order details ( fetch admin cost, and base product prices )

##### Request

Url:

- /orders/histories/{order_id}

Method:

- GET

Params:

- none

##### Response ( Subscriptions)

```json
{
    "data": {
        "id": 1,
        "type": "SUBSCRIPTION",
        "code": "#SB340LM1",
        "subscriptions": {
            "id": 1,
            "name": "Subscription Pertralite 30L",
            "quantity": 30.0,
            "duration_in_days": 30,
            "price": 220000,
        },
        payment: {
            id: 1,
            "method": "LINK_AJA",
            "total": 223000,
            "admin_fee": 3000,
        },
        "product": {
            "id": 2,
            "name": "pertralite",
        },
        "gas_station": {
            "id": 1,
            "name": "31.143.01",
        },
        "created_at": "2019-08-19 11:02:22",
    },
}
```

##### Response ( Petrol )

```json
{
    "data": {
        "id": 2,
        "type": "PETROL",
        "code": "#PS340LM1",
        "subscriptions": null,
        "product": {
            "id": 2,
            "name": "pertralite",
            "price": 7680,
        },
        payment: {
            id: 1,
            "method": "LETS_GAS_SUB",
            "total": 3.13,
        },
        "quantity": 3.13,
        "gas_station": {
            "id": 1,
            "name": "31.143.01",
        },
        "created_at": "2019-08-19 11:02:22",
    },
}
```

