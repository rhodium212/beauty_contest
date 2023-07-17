#### GET /admin/users

- Hak akses: User dengan role 'ADMIN'

- Contoh hasil:
```json
{
  "users": [
    {
      "id": 1,
      "first_name": "John",
      "last_name": "Doe",
      "role": "THERAPIST",
      "email": "john.doe@example.com",
      "avatar": "https://example.com/images/avatars/john_doe.jpg",
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:00:00Z"
    },
    {
      "id": 2,
      "first_name": "Jane",
      "last_name": "Doe",
      "role": "USER",
      "email": "jane.doe@example.com",
      "avatar": "https://example.com/images/avatars/jane_doe.jpg",
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:00:00Z"
    },
    ...
  ]
}
```

#### PUT /admin/users/{user_id}

- Hak akses: User dengan role 'ADMIN'

- Parameter yang dibawa:

```json
{
  "first_name": "John",
  "last_name": "Doe",
  "avatar": "https://example.com/images/avatars/john_doe.jpg",
  "role": "THERAPIST"
}
```

- Contoh hasil:
```json
{
  "id": 1,
  "first_name": "John",
  "last_name": "Doe",
  "email": "john.doe@example.com",
  "avatar": "https://example.com/images/avatars/john_doe.jpg",
  "role": "THERAPIST",
  "created_at": "2023-07-17T10:00:00Z",
  "updated_at": "2023-07-17T10:00:00Z"
}
```

#### POST /admin/services

- Hak akses: User dengan role 'ADMIN'
- Parameter body:
  - `name`: Nama layanan
  - `description`: Deskripsi layanan

- Contoh request:
```json
{
  "name": "New Service",
  "description": "This is a new service"
}
```
- Contoh hasil:
```json
{
  "message": "Service successfully created",
  "service": {
      "id": 6,
      "name": "New Service",
      "description": "This is a new service",
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:00:00Z"
  }
}
```

#### GET /admin/services

- Hak akses: User dengan role 'ADMIN'

- Contoh hasil:
```json
{
  "services": [
    {
      "id": 1,
      "name": "Service 1",
      "description": "Description of Service 1",
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:00:00Z"
    },
    ...
  ]
}
```

#### PUT /admin/services/{service_id}

- Hak akses: User dengan role 'ADMIN'
- Parameter path:
  - `service_id`: `id` dari layanan yang akan di-update
- Parameter body:
  - `name`: Nama layanan baru
  - `description`: Deskripsi layanan baru

- Contoh request:
```json
{
  "name": "Updated Service",
  "description": "This is an updated service"
}
```
- Contoh hasil:
```json
{
  "message": "Service successfully updated",
  "service": {
      "id": 1,
      "name": "Updated Service",
      "description": "This is an updated service",
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:10:00Z"
  }
}
```

#### DELETE /admin/services/{service_id}

- Hak akses: User dengan role 'ADMIN'
- Parameter path:
  - `service_id`: `id` dari layanan yang akan dihapus

- Contoh hasil:
```json
{
  "message": "Service successfully deleted",
  "deleted_service_id": 1
}
```


#### GET /admin/therapists

- Hak akses: Hanya User dengan role 'ADMIN'

- Parameter: Tidak ada parameter

- Contoh hasil:
```json
[
  {
    "therapist": {
      "id": 1,
      "first_name": "John",
      "last_name": "Doe",
      "email": "john.doe@example.com",
      "avatar": "https://example.com/images/avatars/john_doe.jpg",
      "role": "THERAPIST",
      "location": "POINT(-71.060316, 48.432044)",
      "experience_years": 5,
      "birthdate": "1980-01-01",
      "gender": "MALE",
      "average_rating": 4.5,
      "balance": 1000000,
      "is_available": true,
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:00:00Z"
    },
    "services": [
      {
        "service_id": 1,
        "name": "Deep Tissue Massage",
        "description": "Deep Tissue Massage is a type of massage therapy that focuses on realigning deeper layers of muscles and connective tissue. It is especially helpful for chronic aches and pains and contracted areas."
      },
      {
        "service_id": 2,
        "name": "Hot Stone Massage",
        "description": "Hot Stone Massage is a form of massage therapy that follows the same principles of Swedish Massage with the addition of heated stones, which helps lead to deep relaxation. Adding heat to specific areas on the body enhances the feelings of relaxation and peace."
      }
    ]
  },
  {
    "therapist": {
      "id": 2,
      "first_name": "Jane",
      "last_name": "Doe",
      "email": "jane.doe@example.com",
      "avatar": "https://example.com/images/avatars/jane_doe.jpg",
      "role": "THERAPIST",
      "location": "POINT(-71.110733, 48.512604)",
      "experience_years": 3,
      "birthdate": "1982-05-10",
      "gender": "FEMALE",
      "average_rating": 5,
      "balance": 2000000,
      "is_available": true,
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T10:00:00Z"
    },
    "services": [
      {
        "service_id": 1,
        "name": "Deep Tissue Massage",
        "description": "Deep Tissue Massage is a type of massage therapy that focuses on realigning deeper layers of muscles and connective tissue. It is especially helpful for chronic aches and pains and contracted areas."
      }
    ]
  }
]
```


#### GET /admin/activity_history

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter: Tidak ada parameter

- Contoh hasil:

```json
{
  "activity_history": [
    {
      "id": 1,
      "user_id": 1,
      "user_first_name": "John",
      "user_last_name": "Doe",
      "user_email": "john.doe@example.com",
      "action": "LOGIN",
      "timestamp": "2023-07-17T10:00:00Z",
      "ip_address": "192.0.2.1",
      "device": "Chrome on Windows 10",
      "location": {"type": "Point", "coordinates": [106.865036, -6.175110]} // Longitude, Latitude
    },
    {
      "id": 2,
      "user_id": 1,
      "user_first_name": "John",
      "user_last_name": "Doe",
      "user_email": "john.doe@example.com",
      "action": "UPDATE_PROFILE",
      "timestamp": "2023-07-17T10:30:00Z",
      "ip_address": "192.0.2.1",
      "device": "Chrome on Windows 10",
      "location": {"type": "Point", "coordinates": [106.865036, -6.175110]} // Longitude, Latitude
    },
    //...other activities
  ]
}
```

#### GET /admin/activity_history/{id}

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter: 
  - `{id}`: ID aktivitas yang ingin ditampilkan (path parameter)

- Contoh hasil:

```json
{
  "activity": {
    "id": 1,
    "user_id": 1,
    "user_first_name": "John",
    "user_last_name": "Doe",
    "user_email": "john.doe@example.com",
    "action": "LOGIN",
    "timestamp": "2023-07-17T10:00:00Z",
    "ip_address": "192.0.2.1",
    "device": "Chrome on Windows 10",
    "location": {"type": "Point", "coordinates": [106.865036, -6.175110]}
  }
}
```

#### GET /admin/orders

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter: Tidak ada parameter

- Contoh hasil:

```json
{
  "orders": [
    {
      "id": 1,
      "user_id": 1,
      "user_email": "john.doe@example.com",
      "user_first_name": "John",
      "user_last_name": "Doe",
      "therapist_id": 2,
      "therapist_name": "Jane Doe",
      "service_id": 1,
      "service_name": "Deep Tissue Massage",
      "service_price": 200000,
      "service_duration": 60,
      "order_status": "PAID",
      "appointment_date": "2023-07-17T15:00:00Z",
      "location": {"type": "Point", "coordinates": [106.865036, -6.175110]},
      "payment_status": "SUCCESS",
      "created_at": "2023-07-17T10:00:00Z"
    },
    //...other orders
  ]
}
```

#### GET /admin/orders/{id}

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter:
  - `{id}`: ID pesanan yang ingin ditampilkan (path parameter)

- Contoh hasil:

```json
{
  "order": {
    "id": 1,
    "user": {
      "id": 1,
      "first_name": "John",
      "last_name": "Doe",
      "email": "john.doe@example.com"
    },
    "therapist": {
      "id": 2,
      "user_id": 3,
      "location": {"type": "Point", "coordinates": [106.865036, -6.175110]},
      "experience_years": 3,
      "photo": "https://example.com/images/therapists/jane_doe.jpg",
      "birthdate": "1982-05-10",
      "gender": "FEMALE",
      "is_available": true,
      "created_at": "2023-07-17T10:00:00Z",
      "updated_at": "2023-07-17T11:00:00Z"
    },
    "service": {
      "id": 1,
      "name": "Deep Tissue Massage",
      "description": "Deep Tissue Massage is a type of massage therapy that focuses on realigning deeper layers of muscles and connective tissue. It is especially helpful for chronic aches and pains and contracted areas.",
      "price_per_hour": 200000,
      "image": "https://example.com/images/services/deep_tissue_massage.jpg",
      "minimum_duration": 60
    },
    "order_status": "PAID",
    "appointment_date": "2023-07-17T15:00:00Z",
    "appointment_duration": 60,
    "total_price": 200000,
    "rating": 4,
    "location": {"type": "Point", "coordinates": [106.865036, -6.175110]},
    "note": "Please bring your own towel.",
    "created_at": "2023-07-17T10:00:00Z",
    "updated_at": "2023-07-17T11:00:00Z",
    "payment": {
      "id": 1,
      "order_id": 1,
      "user_id": 1,
      "payment_method": "OVO",
      "payment_status": "SUCCESS",
      "amount_paid": 200000,
      "to_account": "john.doe@example.com",
      "sender_account": "jane.doe@example.com",
      "payment_expired": "2023-07-17T12:00:00Z",
      "payment_at": "2023-07-17T11:30:00Z",
      "created_at": "2023-07-17T10:30:00Z",
      "updated_at": "2023-07-17T11:30:00Z"
    }
  }
}
```

#### GET /admin/therapists/{therapist_id}/ratings

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter:
  - `{therapist_id}`: ID terapis yang ingin ditampilkan riwayat ratingnya (path parameter)

- Contoh hasil:

```json
{
  "ratings": [
    {
      "id": 1,
      "user": {
        "id": 3,
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@example.com"
      },
      "therapist": {
        "id": 2,
        "user_id": 4,
        "first_name": "Jane",
        "last_name": "Doe",
        "email": "jane.doe@example.com"
      },
      "order_id": 1,
      "service": {
        "id": 1,
        "name": "Deep Tissue Massage",
        "description": "Deep Tissue Massage is a type of massage therapy that focuses on realigning deeper layers of muscles and connective tissue. It is especially helpful for chronic aches and pains and contracted areas."
      },
      "rating": 4,
      "note": "Great service!",
      "created_at": "2023-07-17T11:30:00Z",
      "updated_at": "2023-07-17T11:30:00Z"
    },
    //...other ratings
  ]
}
```

#### GET /admin/payments

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter: Tidak ada parameter

- Contoh hasil:

```json
{
  "payments": [
    {
      "id": 1,
      "order_id": 1,
      "user": {
        "id": 3,
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@example.com"
      },
      "payment_method": "OVO",
      "payment_status": "SUCCESS",
      "amount_paid": 200000,
      "to_account": "john.doe@example.com",
      "sender_account": "jane.doe@example.com",
      "payment_expired": "2023-07-17T12:00:00Z",
      "payment_at": "2023-07-17T11:30:00Z",
      "created_at": "2023-07-17T10:30:00Z",
      "updated_at": "2023-07-17T11:30:00Z"
    },
    //...other payments
  ],
  "total_revenue": 500000
}
```

#### GET /admin/payments

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter: Tidak ada parameter

- Contoh hasil:

```json
{
  "payments": [
    {
      "id": 1,
      "order_id": 1,
      "user": {
        "id": 3,
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@example.com"
      },
      "therapist": {
        "id": 2,
        "user_id": 4,
        "first_name": "Jane",
        "last_name": "Doe",
        "email": "jane.doe@example.com"
      },
      "service": {
        "id": 1,
        "name": "Deep Tissue Massage",
        "description": "Deep Tissue Massage is a type of massage therapy that focuses on realigning deeper layers of muscles and connective tissue. It is especially helpful for chronic aches and pains and contracted areas.",
        "price_per_hour": 200000,
        "image": "https://example.com/images/services/deep_tissue_massage.jpg",
        "minimum_duration": 60
      },
      "payment_method": "OVO",
      "payment_status": "SUCCESS",
      "amount_paid": 200000,
      "to_account": "john.doe@example.com",
      "sender_account": "jane.doe@example.com",
      "payment_expired": "2023-07-17T12:00:00Z",
      "payment_at": "2023-07-17T11:30:00Z",
      "created_at": "2023-07-17T10:30:00Z",
      "updated_at": "2023-07-17T11:30:00Z",
      "order_duration": 90
    },
    //...other payments
  ],
  "total_revenue": 500000
}
```

#### GET /admin/users/balance

- Hak akses: Hanya admin (auth token diperlukan)

- Parameter: Tidak ada parameter

- Contoh hasil:

```json
{
  "balances": [
    {
      "user": {
        "id": 1,
        "first_name": "John",
        "last_name": "Doe",
        "email": "john.doe@example.com"
      },
      "balance_amount": 500000
    },
    {
      "user": {
        "id": 2,
        "first_name": "Jane",
        "last_name": "Smith",
        "email": "jane.smith@example.com"
      },
      "balance_amount": 300000
    },
    //...other balances
  ]
}
```
