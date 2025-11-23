# GiftAsset API Documentation
## ⚙️ [SWAGGER](https://giftasset.pro/docs)
## 🟢 [STATUS CODES](https://github.com/GIFT-ASSET/gift_asset_api/blob/main/status/HTTP_STATUS_CODES.md)
## 🧰 [PYTHON-SDK](https://github.com/GIFT-ASSET/gift_asset_api/blob/main/python_sdk/README.md)
**Base URL:** https://giftasset.pro  

---

## Contents

- [User-Data](#user-data)  
- [Providers](#providers)  
- [Metadata](#metadata)  
- [Analytics](#analytics)  

---

# User-Data

---

## Receive all user's collections gifts

**POST** `/api/v1/gifts/get_all_collections_by_user`

**Query Parameters:**

- `username` *(string, required)* — Telegram username

**Request Body (optional):**
```json
{
  "include": ["Evil Eye"],
  "exclude": ["Evil Eye"],
  "limit": 100,
  "offset": 0
}
```
- `include` *(array of strings)* — Only the specified collections  
- `exclude` *(array of strings)* — All except the specified collections  
- `limit` *(integer)* — Limit of returned gifts  
- `offset` *(integer)* — Offset (pagination)  

**Responses:**

- `200 OK` — Successfully retrieved user's collections gifts  
```json
[
  {
    "collection_name": "Lunar Snake",
    "count": 1
  }
]
```
- `400 Bad Request` — Invalid parameters  
```json
{
  "code": "PARAM_MISSING",
  "message": "Missing 'username' parameter"
}
```
- `401 Unauthorized` — Invalid API key  
```json
{
  "code": "UNAUTHORIZED",
  "message": "Invalid or inactive API key"
}
```
- `422 Unprocessable Entity` — Validation error for collection names  
```json
{
  "code": "VALIDATION_ERROR",
  "message": "Invalid collection names provided",
  "details": [
    "Collection 'Invalid Collection' does not exist"
  ]
}
```
- `500 Internal Server Error`  
```json
{
  "code": "INTERNAL_SERVER_ERROR",
  "message": "Internal server error occurred"
}
```

---

## Receive a gift by name

**GET** `/api/v1/gifts/get_gift_by_name`

**Query Parameters:**

- `name` *(string, required)* — Gift name (e.g., `EasterEgg-1`)

**Responses:**

- `200 OK` — Successfully retrieved gift details  
```json
{
  "attributes": {
    "BACKDROP": {
      "media": "https://giftasset.pro/api/v1/data/backdrops/hunter_green.png",
      "name": "Hunter Green",
      "rarity": 12,
      "readable_rarity": 1.2
    },
    "MODEL": {
      "media": "https://giftasset.pro/api/v1/data/models/redwhelp.png",
      "name": "Red Whelp",
      "rarity": 5,
      "readable_rarity": 0.5
    },
    "SYMBOL": {
      "media": "https://giftasset.pro/api/v1/data/symbols/moose_head.png",
      "name": "Moose Head",
      "rarity": 5,
      "readable_rarity": 0.5
    }
  },
  "attributes_array": [
    {
      "name": "Red Whelp",
      "rarity": 0.5,
      "type": "MODEL"
    },
    {
      "name": "Moose Head",
      "rarity": 0.5,
      "type": "SYMBOL"
    },
    {
      "name": "Hunter Green",
      "rarity": 1.2,
      "type": "BACKDROP"
    }
  ],
  "collectible_id": 1,
  "id": 1707,
  "last_updated_at": "2025-08-16T07:14:44Z",
  "market_floor": {
    "avg": 1.933,
    "max": 2,
    "min": 1.9
  },
  "media": {
    "lottie_anim": "https://nft.fragment.com/gift/easteregg-1.lottie.json",
    "pics": {
      "large": "https://nft.fragment.com/gift/easteregg-1.large.jpg",
      "medium": "https://nft.fragment.com/gift/easteregg-1.medium.jpg",
      "small": "https://nft.fragment.com/gift/easteregg-1.small.jpg"
    }
  },
  "media_preview": "https://nft.fragment.com/gift/easteregg-1.medium.jpg",
  "providers": {
    "getgems": {
      "collection_floor": 1.9,
      "model_floor": 15,
      "sales_stat": {
        "sales_24h": 21,
        "sales_24h_value": 85,
        "sales_all": 251,
        "sales_all_value": 997
      }
    },
    "portals": {
      "collection_floor": 1.9,
      "model_floor": 9.7,
      "sales_stat": {
        "sales_24h": 295,
        "sales_24h_value": 881,
        "sales_all": 18309,
        "sales_all_value": 71787
      }
    },
    "tonnel": {
      "collection_floor": 2,
      "model_floor": 10.2,
      "sales_stat": {
        "sales_24h": 68,
        "sales_24h_value": 218,
        "sales_all": 80013,
        "sales_all_value": 327740
      }
    }
  },
  "rarity_index": 0.00003,
  "telegram_gift_id": 5774079931671643000,
  "telegram_gift_name": "EasterEgg-1",
  "telegram_gift_number": 150212,
  "telegram_gift_title": "Easter Egg",
  "telegram_nft_url": "https://t.me/nft/EasterEgg-1",
  "total_amount": 173176
}
```
- `400 Bad Request` — Missing or invalid parameters  
- `401 Unauthorized` — Invalid API key  
- `500 Internal Server Error`

---

## Receive user's gifts

**GET** `/api/v1/gifts/get_gift_by_user`

**Query Parameters:**

- `username` *(string, required)*  
- `limit` *(integer, required)* — Number of gifts to return  
- `offset` *(integer, optional)* — For pagination  

**Responses:**

- `200 OK` — Successfully retrieved user's gifts  
```json
[
  {
    "attributes": {
      "BACKDROP": {
        "media": "https://giftasset.pro/api/v1/data/backdrops/chocolate.png",
        "name": "Chocolate",
        "rarity": 10,
        "readable_rarity": 1
      },
      "MODEL": {
        "media": "https://giftasset.pro/api/v1/data/models/garnet.png",
        "name": "Garnet",
        "rarity": 24,
        "readable_rarity": 2.4
      },
      "SYMBOL": {
        "media": "https://giftasset.pro/api/v1/data/symbols/knight.png",
        "name": "Knight",
        "rarity": 10,
        "readable_rarity": 1
      }
    },
    "attributes_array": [
      {
        "name": "Knight",
        "rarity": 1,
        "type": "SYMBOL"
      },
      {
        "name": "Chocolate",
        "rarity": 1,
        "type": "BACKDROP"
      },
      {
        "name": "Garnet",
        "rarity": 2.4,
        "type": "MODEL"
      }
    ],
    "collectible_id": 2072,
    "id": 692564,
    "last_updated_at": "2025-08-16T07:09:02Z",
    "market_floor": {
      "avg": 80,
      "max": 85,
      "min": 76
    },
    "media": {
      "lottie_anim": "https://nft.fragment.com/gift/astralshard-2072.lottie.json",
      "pics": {
        "large": "https://nft.fragment.com/gift/astralshard-2072.large.jpg",
        "medium": "https://nft.fragment.com/gift/astralshard-2072.medium.jpg",
        "small": "https://nft.fragment.com/gift/astralshard-2072.small.jpg"
      }
    },
    "media_preview": "https://nft.fragment.com/gift/astralshard-2072.medium.jpg",
    "providers": {
      "getgems": {
        "collection_floor": 76,
        "model_floor": 100,
        "sales_stat": {
          "sales_24h": 1,
          "sales_24h_value": 135,
          "sales_all": 24,
          "sales_all_value": 2293
        }
      },
      "portals": {
        "collection_floor": 79,
        "model_floor": 130,
        "sales_stat": {
          "sales_24h": 10,
          "sales_24h_value": 772,
          "sales_all": 1622,
          "sales_all_value": 149899
        }
      },
      "tonnel": {
        "collection_floor": 85,
        "model_floor": 90,
        "sales_stat": {
          "sales_24h": 4,
          "sales_24h_value": 350,
          "sales_all": 2410,
          "sales_all_value": 175386
        }
      }
    },
    "rarity_index": 0.00024,
    "telegram_gift_id": 5830425027807282000,
    "telegram_gift_name": "AstralShard-2072",
    "telegram_gift_number": 5370,
    "telegram_gift_title": "Astral Shard",
    "telegram_nft_url": "https://t.me/nft/AstralShard-2072",
    "total_amount": 6196
  }
]
```

- `400 Bad Request`  
- `401 Unauthorized`  
- `500 Internal Server Error`  

---

## Get the cost of a user's profile

**GET** `/api/v1/gifts/get_user_profile_price`

**Query Parameters:**

- `username` *(string, required)*  
- `limit` *(integer, required)*  
- `offset` *(integer, optional)*  

**Responses:**

- `200 OK`
```json
{
  "gifts": [
    {
      "collection_prices": {
        "getgems": 76,
        "portals": 79,
        "tonnel": 85
      },
      "model_prices": {
        "getgems": 100,
        "portals": 130,
        "tonnel": 90
      },
      "name": "AstralShard-2072"
    }
  ],
  "total_collection_price": {
    "getgems": 76,
    "portals": 79,
    "tonnel": 85
  },
  "total_model_price": {
    "getgems": 100,
    "portals": 130,
    "tonnel": 90
  }
}
```

- Other error codes: `400`, `401`, `500`

---

# Providers

---

## Get the top sales volume of individual attributes per day

**GET** `/api/v1/gifts/get_attribute_volumes`

**Responses:**

- `200 OK`  
```json
{
  "getgems": {
    "backdrops": [
      {
        "collection_name": "Lol Pop",
        "name": "Steel Grey",
        "sales_count": 14,
        "sales_sum": "27.66"
      },
      {
        "collection_name": "B-Day Candle",
        "name": "Ivory White",
        "sales_count": 13,
        "sales_sum": "25.04"
      }
    ]
  }
}
```

- Other error codes: `400`, `401`, `500`

---

## Get collection buy offers

**POST** `/api/v1/gifts/get_collection_offers`

**Request Body:**

```json
{
  "collection_name": "Evil Eye"
}
```

**Responses:**

- `200 OK`  
```json
{
  "portals": [
    {
      "collection_name": "Evil Eye",
      "offer_price": 3.12,
      "offers_count": 2
    },
    {
      "collection_name": "Evil Eye",
      "offer_price": 3.11,
      "offers_count": 2
    }
  ]
}
```

- Other error codes: `400`, `401`, `500`

---

## Get the top sales volume of individual collections per N time

**GET** `/api/v1/gifts/get_custom_collections_volumes`

**Query Parameters:**

- `maxtime` *(integer, required)* — Time in seconds (e.g., 3600)

**Responses:**

- `200 OK`  
```json
{
  "getgems": {
    "collections": [
      {
        "collection_name": "Snoop Dogg",
        "name": "Snoop Dogg",
        "sales_count": 1,
        "sales_sum": "2.00"
      }
    ]
  }
}
```

- Other error codes: `400`, `401`, `500`

---

## Get fee per provider

**GET** `/api/v1/gifts/get_providers_fee`

**Responses:**

- `200 OK`  
```json
[
  {
    "fee": 5,
    "provider": "portals"
  },
  {
    "fee": 3,
    "provider": "tonnel"
  },
  {
    "fee": 0,
    "provider": "getgems"
  }
]
```

- Other error codes: `400`, `401`, `500`

---

## Get sales history of current provider

**GET** `/api/v1/gifts/get_providers_sales_history`

**Query Parameters:**

- `provider_name` *(string, required)*  
- `limit` *(integer, required)*  
- `offset` *(integer, required)*  
- `premarket` *(boolean, optional)*  

**Responses:**

- `200 OK`  
```json
[
  {
    "collection_name": "Jelly Bunny",
    "price": 5,
    "provider": "tonnel",
    "telegram_gift_id": 5965079038585210000,
    "telegram_gift_name": "JellyBunny-56865",
    "telegram_gift_number": 85212,
    "unix_time": 1755428712
  }
]
```

- Other error codes: `400`, `401`, `500`

---

## Get providers' sales volumes

**GET** `/api/v1/gifts/get_providers_volumes`

**Responses:**

- `200 OK`  
```json
[
  {
    "hour_revenue": 7962.049999999991,
    "hour_sales": 1679,
    "peak_hour": "2025-08-16T19:00:00+00:00",
    "peak_hour_revenue_percent": 7.73,
    "peak_hour_sales_percent": 10.65,
    "provider": "portals",
    "total_revenue": 103026.15,
    "total_sales": 15769
  }
]
```

- Other error codes: `400`, `401`, `500`

---

## Get the top deals of the day

**GET** `/api/v1/gifts/get_top_best_deals`

**Responses:**

- `200 OK`  
```json
{
  "getgems": [
    {
      "gift": {
        "attributes": {
          "BACKDROP": {
            "media": "https://giftasset.pro/api/v1/data/backdrops/strawberry.png",
            "name": "Strawberry",
            "rarity": 20,
            "readable_rarity": 2
          },
          "MODEL": {
            "media": "https://giftasset.pro/api/v1/data/models/sketchy.png",
            "name": "Sketchy",
            "rarity": 20,
            "readable_rarity": 2
          },
          "SYMBOL": {
            "media": "https://giftasset.pro/api/v1/data/symbols/boat.png",
            "name": "Boat",
            "rarity": 5,
            "readable_rarity": 0.5
          }
        },
        "attributes_array": [
          {
            "name": "Boat",
            "rarity": 0.5,
            "type": "SYMBOL"
          },
          {
            "name": "Sketchy",
            "rarity": 2,
            "type": "MODEL"
          },
          {
            "name": "Strawberry",
            "rarity": 2,
            "type": "BACKDROP"
          }
        ],
        "collectible_id": 239,
        "id": 811671,
        "last_updated_at": "2025-08-16T07:09:00Z",
        "market_floor": {
          "avg": 3298.667,
          "max": 3688,
          "min": 3079
        },
        "media": {
          "lottie_anim": "https://nft.fragment.com/gift/plushpepe-239.lottie.json",
          "pics": {
            "large": "https://nft.fragment.com/gift/plushpepe-239.large.jpg",
            "medium": "https://nft.fragment.com/gift/plushpepe-239.medium.jpg",
            "small": "https://nft.fragment.com/gift/plushpepe-239.small.jpg"
          }
        },
        "media_preview": "https://nft.fragment.com/gift/plushpepe-239.medium.jpg",
        "providers": {
          "getgems": {
            "collection_floor": 3079,
            "model_floor": null,
            "sales_stat": {
              "sales_24h": 3,
              "sales_24h_value": 9590,
              "sales_all": 53,
              "sales_all_value": 200911
            }
          },
          "portals": {
            "collection_floor": 3129,
            "model_floor": 4399,
            "sales_stat": {
              "sales_24h": 3,
              "sales_24h_value": 11760,
              "sales_all": 411,
              "sales_all_value": 1613905
            }
          },
          "tonnel": {
            "collection_floor": 3688,
            "model_floor": 4000,
            "sales_stat": {
              "sales_24h": 0,
              "sales_24h_value": 0,
              "sales_all": 541,
              "sales_all_value": 906893
            }
          }
        },
        "rarity_index": 0.0002,
        "telegram_gift_id": 6028603284225263000,
        "telegram_gift_name": "PlushPepe-239",
        "telegram_gift_number": 2822,
        "telegram_gift_title": "Plush Pepe",
        "telegram_nft_url": "https://t.me/nft/PlushPepe-239",
        "total_amount": 2861
      },
      "price": 3600,
      "provider": "getgems",
      "type": "deal",
      "unix": 1755351027
    }
  ]
}
```

- Other error codes: `400`, `401`, `500`

---

# Metadata

---

## Get raw information of collection attributes

**GET** `/api/v1/gifts/get_attributes_metadata`

**Responses:**

- `200 OK`  
```json
[
  {
    "collection_name": "Snoop Dogg",
    "telegram_id": 6014591077976114000
  }
]
```

- Other error codes: `400`, `401`, `500`

---

## Get raw information of collections

**GET** `/api/v1/gifts/get_collections_metadata`

**Responses:**

- `200 OK`  
```json
[
  {
    "collection_name": "Snoop Dogg",
    "telegram_id": 6014591077976114000
  }
]
```

- Other error codes: `400`, `401`, `500`

---

# Analytics

---

## Get an issue of unique gifts inside collections

**GET** `/api/v1/gifts/get_gifts_collections_emission`

**Responses:**

- `200 OK`  
```json
{
  "Astral Shard": {
    "emission": 6196,
    "upgraded": 5391
  },
  "Berry Box": {
    "emission": 66580,
    "upgraded": 42716
  }
}
```

- Other error codes: `400`, `401`, `500`

---

## Get the market-cap of gifts

**GET** `/api/v1/gifts/get_gifts_collections_marketcap`

**Responses:**

- `200 OK`  
```json
{
  "getgems": [
    {
      "available_gifts": 5359,
      "collection_name": "Astral Shard",
      "floor": "85.00",
      "ton_mcap": 455515
    }
  ]
}
```

- Other error codes: `400`, `401`, `500`

---

## Get statistics on gift improvements per day

**GET** `/api/v1/gifts/get_gifts_update_stat`

**Responses:**

- `200 OK`  
```json
{
  "last_updates": [
    {
      "gift_name": "PartySparkler-136662",
      "unix_time": 1754557963
    },
    {
      "gift_name": "SnakeBox-106895",
      "unix_time": 1754557963
    }
  ]
}
```

- Other error codes: `400`, `401`, `500`

---
