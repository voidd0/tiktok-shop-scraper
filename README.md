# TikTok Shop Scraper: export to CSV or JSON with Python, Node.js or curl

Scrape TikTok Shop product pages in the United States from product links or IDs: title, price, original price, discount, units sold, rating, review count, stock, variants, images, category, shipping and shop details. No reviews or creator data. Not affiliated with TikTok.

This repository has ready scripts for the [TikTok Shop Scraper: Products, Units Sold | $2.70 per 1,000](https://apify.com/v0iddo/tiktok-shop-product-scraper) Actor on Apify. The Actor does the
fetching, paging and cleaning; the scripts here run it with your input and save the results as a CSV or JSON file.

## Quick start

1. Create an Apify account and copy your API token from
   [Console > Settings > Integrations](https://console.apify.com/settings/integrations).
2. Install the client and run the script with the example input:

```bash
pip install "apify-client>=2"
export APIFY_TOKEN=your_token
python run.py input.json -o results.csv --max-items 50
```

Edit `input.json` for your own run. You can also run the Actor in the browser on its
[Apify page](https://apify.com/v0iddo/tiktok-shop-product-scraper), schedule it there, and connect its output to Google Sheets, Slack, Zapier or Make.

## Input

The example input (`input.json`):

```json
{
  "products": [
    "https://shop.tiktok.com/us/pdp/cat-nail-clipper-by-potaroma-adjustable-sizes-built-in-file-safe-for-kittens-cats/1731578642912612516",
    "https://shop.tiktok.com/us/pdp/zila-cropped-cable-knit-top-100-cotton-front-button-closures/1732500518270439586",
    "https://shop.tiktok.com/us/pdp/jetech-matte-case-for-iphone-16-shockproof-anti-fingerprint/1732347639758557964",
    "https://shop.tiktok.com/us/pdp/jetech-screen-protector-for-ipad-a16-9h-tempered-glass-2-pack/1732359237559685900",
    "https://shop.tiktok.com/us/pdp/waterproof-mascara-by-sace-lady/1730219123026333900",
    "https://shop.tiktok.com/us/pdp/deodorant-truly-beauty-unicorn-fruit-cotton-candy-scent-for-bright-skin/1729430515554816714",
    "https://shop.tiktok.com/us/pdp/womens-bucket-hat-by-unknown-colorblock-knit-warm-fisherman-style/1729721254514234223",
    "https://shop.tiktok.com/us/pdp/ashwagandha-gummies-by-goli-ksm-66-mixed-berry-vegan-non-gmo/1729527313880355335",
    "https://shop.tiktok.com/us/pdp/eskute-v101-1500w-electric-bike-28mph-85mi-range-7-speed/1729506602529690818",
    "https://shop.tiktok.com/us/pdp/centella-green-tea-hydrating-gel-cleanser-gentle-daily-use/1729449803340812401"
  ],
  "maxItems": 20
}
```

| Field | Type | What it does |
| --- | --- | --- |
| `products` | array | TikTok Shop product links such as https://shop.tiktok.com/us/pdp/product-name/1731578642912612516 or https://www.tiktok.com/shop/pdp/1731578642912612516, or... |
| `maxItems` | integer | The run stops after this many result rows. |

## Output

One row per result. A real row from a run of the example input (more in
[`examples/sample-output.json`](examples/sample-output.json)):

```json
{
  "productId": "1731578642912612516",
  "url": "https://shop.tiktok.com/us/pdp/cat-nail-clipper-by-potaroma-adjustable-sizes-built-in-file-safe-for-kittens-cats/1731578642912612516",
  "region": "US",
  "title": "Potaroma Universal Cat Paw Trimmer - ABS Plastic, 1mm to 3.5mm 4-Size Adjustable Holes, Hidden Nail File, Anti-Splash Clean Design, Lockable Storage, Safe Travel-Friendly Home Grooming Tool (Blue)",
  "status": "on_sale",
  "inStock": true,
  "price": 12.97,
  "priceMax": 12.97,
  "originalPrice": 26,
  "discountPercent": 50,
  "currency": "USD",
  "priceText": "$12.97",
  "soldCount": 17022,
  "rating": 4.4,
  "reviewCount": 1449,
  "ratingCounts": {
    "1": 95,
    "2": 49,
    "3": 88,
    "4": 171,
    "5": 1046
  },
  "shopName": "Potaroma LLC",
  "shopId": "7495813075786500260",
  "shopUrl": "https://shop.tiktok.com/us/store/potaroma-llc/7495813075786500260",
  "shopRating": 4.4,
  "shopSoldCount": 216397,
  "shopProductCount": 66,
  "shopFollowerCount": 13498,
  "shopScores": [
    {
      "name": "Positive feedback",
      "value": "86%"
    },
    {
      "name": "Issue resolution",
      "value": "<7h"
    },
    {
      "name": "Chat satisfaction",
      "value": "84%"
    }
  ],
  "category": "Claw Care",
  "categoryId": "817544",
  "categories": [
    "Pet Supplies",
    "Dog & Cat Grooming",
    "Claw Care"
  ],
  "mainImage": "https://p16-oec-general-useast5.ttcdn-us.com/tos-useast5-i-omjb5zjo8w-tx/f8b4429c891246468abacbfb08a610fc~tplv-fhlh96nyum-crop-webp:800:800.webp?dr=12190&t=555f072d&ps=933b5bde&shp=c940a200&shcp=9b759fb9&idc=useast5&from=3376456192",
  "images": [
    "https://p16-oec-general-useast5.ttcdn-us.com/tos-useast5-i-omjb5zjo8w-tx/f8b4429c891246468abacbfb08a610fc~tplv-fhlh96nyum-crop-webp:800:800.webp?dr=12190&t=555f072d&ps=933b5bde&shp=c940a200&shcp=9b759fb9&idc=useast5&from=3376456192",
    "https://p16-oec-general-useast5.ttcdn-us.com/tos-useast5-i-omjb5zjo8w-tx/fd59afa10ff7417ca2d6fac0b649424b~tplv-fhlh96nyum-crop-webp:800:800.webp?dr=12190&t=555f072d&ps=933b5bde&shp=c940a200&shcp=9b759fb9&idc=useast5&from=3376456192",
    "https://p16-oec-general-useast5.ttcdn-us.com/tos-useast5-i-omjb5zjo8w-tx/953365009dd74c6e9a1c9309e6abf4b3~tplv-fhlh96nyum-crop-webp:800:800.webp?dr=12190&t=555f072d&ps=933b5bde&shp=c940a200&shcp=9b759fb9&idc=useast5&from=3376456192",
    "https://p16-oec-general-useast5.ttcdn-us.com/tos-useast5-i-omjb5zjo8w-tx/7368533b225645169efc87bd6b1dc461~tplv-fhlh96nyum-crop-webp:800:800.webp?dr=12190&t=555f072d&ps=933b5bde&shp=c940a200&shcp=9b759fb9&idc=useast5&from=3376456192",
    "https://p16-oec-general-useast5.ttcdn-us.com/tos-useast5-i-omjb5zjo8w-tx/2b7450c7e29f44a586c239745cf41a45~tplv-fhlh96nyum-crop-webp:800:800.webp?dr=12190&t=555f072d&ps=933b5bde&shp=c940a200&shcp=9b759fb9&idc=useast5&from=3376456192"
  ],
  "description": "Adjustable Trimmer for All Cat Sizes: This cat nail clipper features a single round trimming hole with 4 adjustable sizes (1–3.5mm diameter), allowing precise control for trimming claws. Whether you’re caring for small kittens or larger indoor cats, the flexible design ensures...",
  "specifications": [
    {
      "name": "Benefit",
      "value": "Clean"
    },
    {
      "name": "Pet type",
      "value": "Cats"
    },
    {
      "name": "Pet supplies type",
      "value": "Nail grinder"
    },
    {
      "name": "Pet size",
      "value": "Universal"
    },
    {
      "name": "Material",
      "value": "ABS"
    }
  ],
  "variants": [
    {
      "skuId": "1731578664610402468",
      "options": [
        {
          "name": "Specifications",
          "value": "Default"
        }
      ],
      "price": 12.97,
      "originalPrice": 26,
      "stock": 22,
      "available": true
    }
  ],
  "variantCount": 1,
  "shippingFee": 0,
  "deliveryMinDays": 4,
  "deliveryMaxDays": 7,
  "deliveryEstimate": "Nov 5 - Nov 8",
  "promotionLabels": [
    "Flash sale",
    "Free shipping"
  ],
  "input": "https://shop.tiktok.com/us/pdp/cat-nail-clipper-by-potaroma-adjustable-sizes-built-in-file-safe-for-kittens-cats/1731578642912612516",
  "scrapedAt": "2026-11-02T02:41:39+00:00"
}
```

Fields: `productId`, `url`, `region`, `title`, `status`, `inStock`, `price`, `priceMax`, `originalPrice`, `discountPercent`, `currency`, `priceText`, `soldCount`, `rating`, `reviewCount`, `ratingCounts`, `shopName`, `shopId`, `shopUrl`, `shopRating`, `shopSoldCount`, `shopProductCount`, `shopFollowerCount`, `shopScores`, `category`, `categoryId`, `categories`, `mainImage`, `images`, `description`, `specifications`, `variants`, `variantCount`, `shippingFee`, `deliveryMinDays`, `deliveryMaxDays`, `deliveryEstimate`, `promotionLabels`, `input`, `scrapedAt`.

## Node.js

```javascript
import { ApifyClient } from 'apify-client';

const client = new ApifyClient({ token: process.env.APIFY_TOKEN });
const run = await client.actor('v0iddo/tiktok-shop-product-scraper').call({"products": ["https://shop.tiktok.com/us/pdp/cat-nail-clipper-by-potaroma-adjustable-sizes-built-in-file-safe-for-kittens-cats/1731578642912612516", "https://shop.tiktok.com/us/pdp/zila-cropped-cable-knit-top-100-cotton-front-button-closures/1732500518270439586", "https://shop.tiktok.com/us/pdp/jetech-matte-case-for-iphone-16-shockproof-anti-fingerprint/1732347639758557964", "https://shop.tiktok.com/us/pdp/jetech-screen-protector-for-ipad-a16-9h-tempered-glass-2-pack/1732359237559685900", "https://shop.tiktok.com/us/pdp/waterproof-mascara-by-sace-lady/1730219123026333900", "https://shop.tiktok.com/us/pdp/deodorant-truly-beauty-unicorn-fruit-cotton-candy-scent-for-bright-skin/1729430515554816714", "https://shop.tiktok.com/us/pdp/womens-bucket-hat-by-unknown-colorblock-knit-warm-fisherman-style/1729721254514234223", "https://shop.tiktok.com/us/pdp/ashwagandha-gummies-by-goli-ksm-66-mixed-berry-vegan-non-gmo/1729527313880355335", "https://shop.tiktok.com/us/pdp/eskute-v101-1500w-electric-bike-28mph-85mi-range-7-speed/1729506602529690818", "https://shop.tiktok.com/us/pdp/centella-green-tea-hydrating-gel-cleanser-gentle-daily-use/1729449803340812401"], "maxItems": 20});
const { items } = await client.dataset(run.defaultDatasetId).listItems();
```

Full example: [`examples/node/run.mjs`](examples/node/run.mjs).

## Any language: one HTTP request

```bash
curl -X POST "https://api.apify.com/v2/acts/v0iddo~tiktok-shop-product-scraper/run-sync-get-dataset-items" \
  -H "Authorization: Bearer $APIFY_TOKEN" -H 'Content-Type: application/json' \
  -d '{"products": ["https://shop.tiktok.com/us/pdp/cat-nail-clipper-by-potaroma-adjustable-sizes-built-in-file-safe-for-kittens-cats/1731578642912612516", "https://shop.tiktok.com/us/pdp/zila-cropped-cable-knit-top-100-cotton-front-button-closures/1732500518270439586", "https://shop.tiktok.com/us/pdp/jetech-matte-case-for-iphone-16-shockproof-anti-fingerprint/1732347639758557964", "https://shop.tiktok.com/us/pdp/jetech-screen-protector-for-ipad-a16-9h-tempered-glass-2-pack/1732359237559685900", "https://shop.tiktok.com/us/pdp/waterproof-mascara-by-sace-lady/1730219123026333900", "https://shop.tiktok.com/us/pdp/deodorant-truly-beauty-unicorn-fruit-cotton-candy-scent-for-bright-skin/1729430515554816714", "https://shop.tiktok.com/us/pdp/womens-bucket-hat-by-unknown-colorblock-knit-warm-fisherman-style/1729721254514234223", "https://shop.tiktok.com/us/pdp/ashwagandha-gummies-by-goli-ksm-66-mixed-berry-vegan-non-gmo/1729527313880355335", "https://shop.tiktok.com/us/pdp/eskute-v101-1500w-electric-bike-28mph-85mi-range-7-speed/1729506602529690818", "https://shop.tiktok.com/us/pdp/centella-green-tea-hydrating-gel-cleanser-gentle-daily-use/1729449803340812401"], "maxItems": 20}'
```

The response is the JSON array of results.

## Cost

The Actor is paid per result: **$2.70 per 1,000 results**, nothing per run. `maxItems` caps the rows, and so the cost, of one run. A new Apify account gets $5 of platform credit every month.

## License

MIT for the code in this repository. Made by [vøiddo](https://voiddo.com).
