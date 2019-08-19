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
    data: [
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

