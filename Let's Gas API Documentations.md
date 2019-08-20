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



## 1. Stations ( Workshops / Gas )

Base URL: /stations/

#### Get All Nearest Gas Stations

##### Request

Url:

- /stations/:type/

Method:

- GET

Params:

- type: 
  - GAS_STATION
  - WORKSHOP

Queries:

- lat: float value of latitude
- lng: float value of longitude

##### Response ( GAS_STATION )

```json
{
    "next": "/stations/GAS_STATION/?lat=-6.23301&lng=121.18123&page=2",
    "prev": null,
    "total_page": 2,
    "total_item": 11,
    "data": [
    {
      "products": [
        {
          "_id": "5d5bb3725c39f75cc5c2a9be",
          "name": "Pertamina Dex",
          "price": 11700,
          "is_deleted": false,
          "created_at": "2019-08-20T08:46:42.681Z",
          "updated_at": "2019-08-20T08:46:42.681Z",
          "__v": 0
        }
      ],
      "facilities": [
        {
          "_id": "5d5b134510d8500943d06336",
          "name": "Toilet",
          "icon": "wc",
          "is_deleted": false,
          "created_at": "2019-08-19T21:23:17.522Z",
          "updated_at": "2019-08-19T21:23:17.522Z",
          "__v": 0
        },
        {
          "_id": "5d5b13f210d8500943d06339",
          "name": "Restoran",
          "icon": "restaurant",
          "is_deleted": false,
          "created_at": "2019-08-19T21:26:10.250Z",
          "updated_at": "2019-08-19T21:26:10.250Z",
          "__v": 0
        },
        {
          "_id": "5d5b141e10d8500943d0633a",
          "name": "Mini Market",
          "icon": "local_convenience_store",
          "is_deleted": false,
          "created_at": "2019-08-19T21:26:54.228Z",
          "updated_at": "2019-08-19T21:26:54.228Z",
          "__v": 0
        }
      ],
      "_id": "5d5bcbbdef60f8700ed45eab",
      "name": "31.143.01",
      "address": "Jalan Limo Kebayoran Lama, Grogol Utara, Jakarta Selatan, 12220",
      "lat": -6.2280988,
      "lng": 106.8060391,
      "open_at": "08:00",
      "closed_at": "21:30",
      "created_at": "2019-08-20T10:30:21.114Z",
      "updated_at": "2019-08-20T12:21:44.109Z",
      "__v": 0,
      "type": "GAS_STATION"
    }
  ]
}
```

##### Response ( WORKSHOP )

```json
{
    "next": "/stations/WORKSHOP/?lat=-6.23301&lng=121.18123&page=2",
    "prev": null,
    "total_page": 2,
    "total_item": 11,
    "data": [
        {
            "id": 1,
            "address": "Jalan Limo Kebayoran Lama, Grogol Utara, Jakarta Selatan, 12220",
            "photo_url": "https://somebucket.com/ae231cb.png",
            "type": "WORKSHOP",
            "lat": -6.241,
            "lng": 121.19238189,
            "distance": "1.5",
            "open_at": "08:00",
            "closed_at": "21:00",
            "is_open": true,
            "name": "Planet Ban",
            "facilities": [
                {
                    "id": 33,
                    "name": "Toilet",
                    "icon": "https://somebucket.com/ce811fe.png",
                    "is_available": true,
                },
            ],
            "products": [
                {
                    "id": 1211,
                    "name": "Service Kecil",
                    "price": 35000,
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

- /stations/{gas_station_id}

Method:

- GET

Params:

- none

##### Response

```json
{
    "data": {
    "products": [
      {
        "_id": "5d5bb3725c39f75cc5c2a9be",
        "name": "Pertamina Dex",
        "price": 11700,
        "is_deleted": false,
        "created_at": "2019-08-20T08:46:42.681Z",
        "updated_at": "2019-08-20T08:46:42.681Z",
        "__v": 0
      }
    ],
    "facilities": [
      {
        "_id": "5d5b134510d8500943d06336",
        "name": "Toilet",
        "icon": "wc",
        "is_deleted": false,
        "created_at": "2019-08-19T21:23:17.522Z",
        "updated_at": "2019-08-19T21:23:17.522Z",
        "__v": 0
      },
      {
        "_id": "5d5b13f210d8500943d06339",
        "name": "Restoran",
        "icon": "restaurant",
        "is_deleted": false,
        "created_at": "2019-08-19T21:26:10.250Z",
        "updated_at": "2019-08-19T21:26:10.250Z",
        "__v": 0
      },
      {
        "_id": "5d5b141e10d8500943d0633a",
        "name": "Mini Market",
        "icon": "local_convenience_store",
        "is_deleted": false,
        "created_at": "2019-08-19T21:26:54.228Z",
        "updated_at": "2019-08-19T21:26:54.228Z",
        "__v": 0
      }
    ],
    "_id": "5d5bcbbdef60f8700ed45eab",
    "name": "31.143.01",
    "address": "Jalan Limo Kebayoran Lama, Grogol Utara, Jakarta Selatan, 12220",
    "lat": -6.2280988,
    "lng": 106.8060391,
    "open_at": "08:00",
    "closed_at": "21:30",
    "created_at": "2019-08-20T10:30:21.114Z",
    "updated_at": "2019-08-20T12:20:09.285Z",
    "__v": 0,
    "type": "GAS_STATION"
  }
}
```

##### Response ( WORKSHOP )

```json
{
    "next": "/stations/1/?lat=-6.23301&lng=121.18123&page=2",
    "prev": null,
    "total_page": 2,
    "total_item": 11,
    "data":[
    {
      "products": [
        {
          "_id": "5d5bb3725c39f75cc5c2a9be",
          "name": "Pertamina Dex",
          "price": 11700,
          "is_deleted": false,
          "created_at": "2019-08-20T08:46:42.681Z",
          "updated_at": "2019-08-20T08:46:42.681Z",
          "__v": 0
        }
      ],
      "facilities": [
        {
          "_id": "5d5b134510d8500943d06336",
          "name": "Toilet",
          "icon": "wc",
          "is_deleted": false,
          "created_at": "2019-08-19T21:23:17.522Z",
          "updated_at": "2019-08-19T21:23:17.522Z",
          "__v": 0
        },
        {
          "_id": "5d5b13f210d8500943d06339",
          "name": "Restoran",
          "icon": "restaurant",
          "is_deleted": false,
          "created_at": "2019-08-19T21:26:10.250Z",
          "updated_at": "2019-08-19T21:26:10.250Z",
          "__v": 0
        },
        {
          "_id": "5d5b141e10d8500943d0633a",
          "name": "Mini Market",
          "icon": "local_convenience_store",
          "is_deleted": false,
          "created_at": "2019-08-19T21:26:54.228Z",
          "updated_at": "2019-08-19T21:26:54.228Z",
          "__v": 0
        }
      ],
      "_id": "5d5bdbfeda4c51108055c351",
      "name": "31.143.01",
      "address": "Jalan Selong Kebayoran Baru, Jakarta Selatan, 12220",
      "lat": -6.2280988,
      "lng": 106.8060391,
      "open_at": "08:00",
      "closed_at": "21:30",
      "type": "WORKSHOP",
      "created_at": "2019-08-20T11:39:42.993Z",
      "updated_at": "2019-08-20T11:39:42.993Z",
      "__v": 0
    }
  ]
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

- /orders/{order_id}

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
        "payment": {
            "id": 1,
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



## 3. Bundles ( packets )

Base URL: /bundles/

#### Get all bundles

##### Request

Url:

- /bundles/

Method:

- GET

Params:

- none

##### Response

```json
{
    "next": "/bundles/&page=2",
    "prev": null,
    "total_page": 2,
    "total_item": 11,
    "data":[
    {
      "_id": "5d5bb6603a15895f0b6f1dff",
      "name": "Pertamina Dex 30L",
      "price": 220000,
      "duration_in_days": 30,
      "quantity": 30,
      "is_deleted": false,
      "products": {
        "_id": "5d5bb3725c39f75cc5c2a9be",
        "name": "Pertamina Dex",
        "price": 11700,
        "is_deleted": false,
        "created_at": "2019-08-20T08:46:42.681Z",
        "updated_at": "2019-08-20T08:46:42.681Z",
        "__v": 0
      },
      "created_at": "2019-08-20T08:59:12.048Z",
      "updated_at": "2019-08-20T08:59:12.048Z",
      "__v": 0
    }
  ]
}
```



#### 