# GiftAsset API Documentation
## ⚙️ [SWAGGER](https://giftasset.pro/docs)
## 🟢 [STATUS CODES](https://github.com/GIFT-ASSET/gift_asset_api/blob/main/status/HTTP_STATUS_CODES.md)
## 🧰 [PYTHON-SDK](https://github.com/GIFT-ASSET/gift_asset_api/blob/main/python_sdk/README.md)

### User-Data

- [Receive all user's collections gifts](#receive-all-users-collections-gifts)
- [Receive gift by name](#receive-gift-by-name)
- [Receive user's gifts](#receive-users-gifts)
- [Get the cost of a user's profile](#get-the-cost-of-a-users-profile)

### Providers

- [Get the top sales volume of individual attributes per day](#get-the-top-sales-volume-of-individual-attributes-per-day)
- [Get collection buy offers](#get-collection-buy-offers)
- [Get the top sales volume of individual collections per N time](#get-the-top-sales-volume-of-individual-collections-per-n-time)
- [Get fee per provider](#get-fee-per-provider)
- [Get sales history of current provider](#get-sales-history-of-current-provider)
- [Get providers' sales volumes](#get-providers-sales-volumes)
- [Get the top deals of the day](#get-the-top-deals-of-the-day)
- [Get the unique deals of the providers](#get-the-top-deals-of-the-day)

### Metadata

- [Get attributes metadata](#get-attributes-metadata)
- [Get collections metadata](#get-collections-metadata)

### Analytics

- [Get collections emission](#get-collections-emission)
- [Get gift prices](#get-gift-prices)
- [Get gift price list history](#get-gift-price-list-history)
- [Get gifts update statistics](#get-gifts-update-statistics)
- [Get the marketcap of gifts](#get-the-marketcap-of-gifts)

---

## Receive all user's collections gifts

**POST** `/api/v1/gifts/get_all_collections_by_user`

**Query Parameters:**

- `username` *(string, required)* — Telegram username

**Request Body (optional):**
```json
{
  "include": ["Evil Eye"],
  "exclude": ["Evil Eye"]
}
```
- `include` *(array of strings)* — Only the specified collections  
- `exclude` *(array of strings)* — All except the specified collections  

**Response:**
```json
[
  {
    "collection_name": "Astral Shard",
    "count": 1
  },
  {
    "collection_name": "Sakura Flower",
    "count": 1
  },
  {
    "collection_name": "Big Year",
    "count": 1
  },
  {
    "collection_name": "Top Hat",
    "count": 1
  },
  {
    "collection_name": "Desk Calendar",
    "count": 1
  },
  {
    "collection_name": "Lunar Snake",
    "count": 1
  },
  {
    "collection_name": "Candy Cane",
    "count": 1
  },
  {
    "collection_name": "Swag Bag",
    "count": 1
  },
  {
    "collection_name": "Snoop Dogg",
    "count": 1
  }
]
```

---

## Receive gift by name

**GET** `/api/v1/gifts/get_gift_by_name`

**Query Parameters:**

- `name` *(string, required)* — Gift name (e.g., `EasterEgg-1`)

**Response:** 
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

---

## Receive user's gifts

**GET** `/api/v1/gifts/get_gift_by_user`

**Query Parameters:**

- `username` *(string, required)*
- `limit` *(integer, required)* — How many gifts to return  
- `offset` *(integer, optional)* — For pagination

**Response:**
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

---

## Get the cost of a user's profile

**GET** `/api/v1/gifts/get_user_profile_price`

**Query Parameters:**

- `username` *(string, required)*  
- `limit` *(integer, required)*  
- `offset` *(integer, optional)*  

**Response:**
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

---

## Get the top sales volume of individual attributes per day

**GET** `/api/v1/gifts/get_attribute_volumes`

**Response:**
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
---

## Get collection buy offers

**POST** `/api/v1/gifts/get_collection_offers`

**Request Body:**
```json
{
  "collection_name": "Evil Eye"
}
```
**Response:**
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
---

## Get the top sales volume of individual collections per N time

**GET** `/api/v1/gifts/get_custom_collections_volumes`

**Query Parameters:**

- `maxtime` *(integer, required)* — Time in seconds (e.g., 3600)

**Response:**
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

---

## Get fee per provider

**GET** `/api/v1/gifts/get_providers_fee`

**Response:**
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

---

## Get sales history of current provider

**GET** `/api/v1/gifts/get_providers_sales_history`

**Query Parameters:**

- `provider_name` *(string, required)* — e.g. `tonnel`  
- `limit` *(integer, required)*  
- `offset` *(integer, required)*  

**Response:**
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

---

## Get providers' sales volumes

**GET** `/api/v1/gifts/get_providers_volumes`

**Response:**
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

---

## Get the top deals of the day

**GET** `/api/v1/gifts/get_top_best_deals`

**Response:**
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

---

## Get the unique deals of the providers

**GET** `/api/v1/gifts/get_unique_deals`

**Response:**
```json
{
  "getgems": [
    {
      "gift": {
        "attributes": {
          "BACKDROP": {
            "name": "Battleship Grey",
            "rarity": 12,
            "readable_rarity": 1.2
          },
          "MODEL": {
            "name": "Monkey Mouse",
            "rarity": 20,
            "readable_rarity": 2
          },
          "SYMBOL": {
            "name": "Paper Crane",
            "rarity": 4,
            "readable_rarity": 0.4
          }
        },
        "attributes_array": [
          {
            "name": "Paper Crane",
            "rarity": 0.4,
            "type": "SYMBOL"
          },
          {
            "name": "Battleship Grey",
            "rarity": 1.2,
            "type": "BACKDROP"
          },
          {
            "name": "Monkey Mouse",
            "rarity": 2,
            "type": "MODEL"
          }
        ],
        "collectible_id": 21755,
        "id": 2083981,
        "last_updated_at": "2025-09-02T08:52:21Z",
        "market_floor": {
          "avg": 1.865,
          "max": 2.56,
          "min": 0
        },
        "media": {
          "lottie_anim": "https://nft.fragment.com/gift/jollychimp-21755.lottie.json",
          "pics": {
            "large": "https://nft.fragment.com/gift/jollychimp-21755.large.jpg",
            "medium": "https://nft.fragment.com/gift/jollychimp-21755.medium.jpg",
            "small": "https://nft.fragment.com/gift/jollychimp-21755.small.jpg"
          }
        },
        "media_preview": "https://nft.fragment.com/gift/jollychimp-21755.medium.jpg",
        "providers": {
          "getgems": {
            "collection_floor": 2.5,
            "sales_stat": {
              "sales_24h": 9,
              "sales_24h_value": 93,
              "sales_all": 9,
              "sales_all_value": 93
            }
          },
          "mrkt": {
            "collection_floor": 2.56,
            "sales_stat": {
              "sales_24h": 202,
              "sales_24h_value": 667,
              "sales_all": 202,
              "sales_all_value": 667
            }
          },
          "portals": {
            "collection_floor": 0,
            "sales_stat": {
              "sales_24h": 1110,
              "sales_24h_value": 5496,
              "sales_all": 1110,
              "sales_all_value": 5496
            }
          },
          "tonnel": {
            "collection_floor": 2.4,
            "sales_stat": {
              "sales_24h": 230,
              "sales_24h_value": 1085,
              "sales_all": 230,
              "sales_all_value": 1085
            }
          }
        },
        "rarity_index": 0.0001,
        "telegram_gift_id": 5825670855492897000,
        "telegram_gift_name": "JollyChimp-21755",
        "telegram_gift_number": 94177,
        "telegram_gift_title": "Jolly Chimp",
        "telegram_nft_url": "https://t.me/nft/JollyChimp-21755",
        "total_amount": 132155
      },
      "price": 25,
      "telegram_gift_name": "JollyChimp-21755",
      "unix": 1756802702
    }
  ]
}
```

---

## Get attributes metadata

**GET** `/api/v1/gifts/get_attributes_metadata`

**Response:**
```json
{
  "Genie Lamp":{
    "backdrops": [],
    "models": [],
    "symbols": []
  }
}
```

---

## Get collections metadata

**GET** `/api/v1/gifts/get_collections_metadata`

**Response:**
```json
[
  {
    "collection_name": "Snoop Dogg",
    "telegram_id": 6014591077976114000
  },
  {
    "collection_name": "Swag Bag",
    "telegram_id": 6012607142387779000
  },
  {
    "collection_name": "Snoop Cigar",
    "telegram_id": 6012435906336654000
  }
]
```

## Get collections emission

**GET** `/api/v1/gifts/get_gifts_collections_emission`

**Response:**
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

---

## Get gift prices

**GET** `/api/v1/gifts/get_gifts_price_list`

**Response:**
```json
{
  "collection_floors": {
    "Astral Shard": {
      "getgems": 76,
      "last_update": "2025-08-17T11:08:44+00:00",
      "portals": 79,
      "tonnel": 84.9
    }
  }
}
```

---

## Get gift price list history

**GET** `/api/v1/gifts/get_gifts_price_list_history`

**Response:**
```json
{
  "Astral Shard": {
    "portals": {
      "24h": {
        "2025-08-16 09:55:36": 74
      },
      "7d": {},
      "current_price": 74
    },
    "tonnel": {
      "24h": {
        "2025-08-16 09:55:37": 73
      },
      "7d": {},
      "current_price": 73
    }
  }
}
```

---

## Get gifts update statistics

**GET** `/api/v1/gifts/get_gifts_update_stat`

**Response:**
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
---

## Get the marketcap of gifts

**GET** `/api/v1/gifts/get_gifts_collections_marketcap`

**Response:**
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
