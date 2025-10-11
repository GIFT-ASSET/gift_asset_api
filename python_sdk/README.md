# GiftAsset SDK Documentation

## 📘 [DOCUMENTATION](https://github.com/GIFT-ASSET/gift_asset_api/blob/main/DOCS.md)
## ⚙️ [SWAGGER](https://giftasset.pro/docs)
## 🟢 [STATUS CODES](https://github.com/GIFT-ASSET/gift_asset_api/blob/main/status/HTTP_STATUS_CODES.md)

> **📝 Note:** All method names in this SDK are identical to those in the Documentation and Swagger. This ensures consistency across all interfaces.
> 
# SDK - HOW TO USE

```python
from giftasset_sdk.giftasset_sdk import SDK
import asyncio

client = SDK(api_key='')

async def main():

  r = await client.get_gifts_update_stat()
  print(r)

asyncio.run(main())
```
## Setup

```bash
pip install giftassetsdk
```
