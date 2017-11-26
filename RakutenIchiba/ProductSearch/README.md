
# Product/Search

## Description

Gets up to 30 products by keywords, genre or product id. Each product can be sold by one or multiple sellers and each shop can have a different price for them.
## Resource URL

https://app.rakuten.co.jp/services/api/Product/Search/20140305
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
keyword<br>*Search keywords* | string | At least one is required | UTF-8 URL encoded string<br>The keyword parameter can have a maximum length of 128 single byte characters<br>The keyword parameter is delimited with single byte space characters. This defaults to an AND operation including all the keywords. To use OR instead set the orFlag to 1.<br>Each search keyword must be at least two single byte characters or one double byte character.<br>An exception is a minimum of two characters if the search keywords are using hiragana, katakana, or symbols.
genreId<br>*Genre ID* | string | At least one is required | ID to specify a genre in Rakuten Ichiba.
productId<br>*Product ID* | string | At least one is required | ID of the product.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.<br>**Default Value:** <code>30</code>
page<br>*Result page* | integer | Optional | An integer between 1 and 100.<br>**Default Value:** <code>1</code>
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.<br>**Valid Values:**<br><code>standard</code> Rakuten standard sort<br><code>-releaseDate</code> <br><code>-seller</code> <br><code>-satisfied</code> <br>**Default Value:** <code>standard</code>
minPrice<br>*Minimum price* | long | Optional | An integer greater than 0 and less than 999,999,999
maxPrice<br>*Maximum price* | long | Optional | An integer greater than 0 and less than 999,999,999<br>maxPrice must be larger than minPrice.
orFlag<br>*OR search flag* | integer | Optional | Choose between AND searches and OR searches when there are multiple keywords.<br>*It isn't possible to use a complex search condition like "(A and B) or C".<br>**Valid Values:**<br><code>0</code> AND<br><code>1</code> OR<br>**Default Value:** <code>0</code>
genreInformationFlag<br>*Genre information flag* | integer | Optional | **Valid Values:**<br><code>0</code> Do not get number of item in each genre.<br><code>1</code> Get number of item in each genre.<br>**Default Value:** <code>0</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/Product/Search/20140305?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=列車&hits=5
### Response

```json
{
  "count": 2492,
  "page": 1,
  "first": 1,
  "last": 5,
  "hits": 5,
  "pageCount": 100,
  "Products": [
    {
      "Product": {
        "productId": "c6a423267274b6ae4fdba858dd1909a0",
        "productName": "アートディンク A列車で行こう9 Ver4.0 マスターズ コンプリートパック",
        "productNo": "",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/c6a423267274b6ae4fdba858dd1909a0/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/c6a423267274b6ae4fdba858dd1909a0/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/001/723/10010004988640001723_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/001/723/10010004988640001723_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "",
        "makerCode": "104988640",
        "makerName": "アートディンク",
        "makerNameKana": "アートデインク",
        "makerNameFormal": "株式会社アートディンク",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/211723/104988640/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/211723/104988640/",
        "itemCount": 15,
        "salesItemCount": 15,
        "usedExcludeCount": 15,
        "usedExcludeSalesItemCount": 15,
        "maxPrice": 19057,
        "salesMaxPrice": 19057,
        "usedExcludeMaxPrice": 19057,
        "usedExcludeSalesMaxPrice": 19057,
        "minPrice": 14790,
        "salesMinPrice": 14790,
        "usedExcludeMinPrice": 14790,
        "usedExcludeSalesMinPrice": 14790,
        "averagePrice": 17078,
        "reviewCount": 2,
        "reviewAverage": 4.5,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/c6a423267274b6ae4fdba858dd1909a0/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/c6a423267274b6ae4fdba858dd1909a0/review/",
        "rank": 13,
        "rankTargetGenreId": "211706",
        "rankTargetProductCount": 5248,
        "genreId": "211723",
        "genreName": "その他",
        "ProductDetails": []
      }
    },
    {
      "Product": {
        "productId": "fa5c46cab237a304b4d32b730bea7807",
        "productName": "アンパンマントロッコ DK-7127",
        "productNo": "DK-7127",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/fa5c46cab237a304b4d32b730bea7807/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/fa5c46cab237a304b4d32b730bea7807/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/971/404/308/664/10010004971404308664_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/971/404/308/664/10010004971404308664_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "",
        "makerCode": "104971404",
        "makerName": "アガツマ",
        "makerNameKana": "アガツマ",
        "makerNameFormal": "株式会社アガツマ",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/101198/104971404/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/101198/104971404/",
        "itemCount": 25,
        "salesItemCount": 18,
        "usedExcludeCount": 25,
        "usedExcludeSalesItemCount": 18,
        "maxPrice": 2669,
        "salesMaxPrice": 2298,
        "usedExcludeMaxPrice": 2669,
        "usedExcludeSalesMaxPrice": 2298,
        "minPrice": 1300,
        "salesMinPrice": 1300,
        "usedExcludeMinPrice": 1300,
        "usedExcludeSalesMinPrice": 1300,
        "averagePrice": 1884,
        "reviewCount": 1,
        "reviewAverage": 5,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/fa5c46cab237a304b4d32b730bea7807/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/fa5c46cab237a304b4d32b730bea7807/review/",
        "rank": 10169,
        "rankTargetGenreId": "207563",
        "rankTargetProductCount": 17707,
        "genreId": "101198",
        "genreName": "その他",
        "ProductDetails": []
      }
    },
    {
      "Product": {
        "productId": "94f5fffc35d5d45bc0c392d6e3d58f5e",
        "productName": "クイニーザップ ベビーカー イッパイツナゴウ EF200セット",
        "productNo": "",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/94f5fffc35d5d45bc0c392d6e3d58f5e/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/94f5fffc35d5d45bc0c392d6e3d58f5e/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/904/810/348/856/10010004904810348856_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/904/810/348/856/10010004904810348856_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "",
        "makerCode": "104904810",
        "makerName": "タカラトミー",
        "makerNameKana": "タカラトミー",
        "makerNameFormal": "株式会社タカラトミー",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/213553/104904810/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/213553/104904810/",
        "itemCount": 13,
        "salesItemCount": 4,
        "usedExcludeCount": 13,
        "usedExcludeSalesItemCount": 4,
        "maxPrice": 9490,
        "salesMaxPrice": 9490,
        "usedExcludeMaxPrice": 9490,
        "usedExcludeSalesMaxPrice": 9490,
        "minPrice": 2800,
        "salesMinPrice": 9074,
        "usedExcludeMinPrice": 2800,
        "usedExcludeSalesMinPrice": 9074,
        "averagePrice": 5753,
        "reviewCount": 1,
        "reviewAverage": 1,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/94f5fffc35d5d45bc0c392d6e3d58f5e/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/94f5fffc35d5d45bc0c392d6e3d58f5e/review/",
        "rank": 3176,
        "rankTargetGenreId": "551256",
        "rankTargetProductCount": 6862,
        "genreId": "213553",
        "genreName": "その他",
        "ProductDetails": [
          {
            "detail": {
              "name": "シリーズ名/愛称",
              "value": "プラレール"
            }
          },
          {
            "detail": {
              "name": "本体サイズ(H×W×D)mm",
              "value": "51×41×1120"
            }
          },
          {
            "detail": {
              "name": "対象年齢",
              "value": "3歳以上"
            }
          },
          {
            "detail": {
              "name": "使用乾電池",
              "value": "単2電池×1本(別売)"
            }
          }
        ]
      }
    },
    {
      "Product": {
        "productId": "11682ec5f5d5cad9c752cb799f973093",
        "productName": "めちゃモテ・サックスアルトサックス A列車で行こう",
        "productNo": "",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/11682ec5f5d5cad9c752cb799f973093/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/11682ec5f5d5cad9c752cb799f973093/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/218/866/361/10010004580218866361_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/218/866/361/10010004580218866361_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "2012年2月17日",
        "makerCode": "10458021886",
        "makerName": "ウィンズスコア",
        "makerNameKana": "ウインズスコア",
        "makerNameFormal": "株式会社ウィンズスコア",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/209332/10458021886/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/209332/10458021886/",
        "itemCount": 5,
        "salesItemCount": 5,
        "usedExcludeCount": 5,
        "usedExcludeSalesItemCount": 5,
        "maxPrice": 1080,
        "salesMaxPrice": 1080,
        "usedExcludeMaxPrice": 1080,
        "usedExcludeSalesMaxPrice": 1080,
        "minPrice": 1080,
        "salesMinPrice": 1080,
        "usedExcludeMinPrice": 1080,
        "usedExcludeSalesMinPrice": 1080,
        "averagePrice": 1080,
        "reviewCount": 0,
        "reviewAverage": 0,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/11682ec5f5d5cad9c752cb799f973093/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/11682ec5f5d5cad9c752cb799f973093/review/",
        "rank": 53068,
        "rankTargetGenreId": "209332",
        "rankTargetProductCount": 134669,
        "genreId": "209332",
        "genreName": "全般",
        "ProductDetails": []
      }
    },
    {
      "Product": {
        "productId": "673ba66b41abdc42e2c0be1091d58240",
        "productName": "A列車で行こう3D 3DS",
        "productNo": "CTRPAALJ",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/673ba66b41abdc42e2c0be1091d58240/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/673ba66b41abdc42e2c0be1091d58240/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/200/034/10010004988640200034_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/200/034/10010004988640200034_1.jpg?_ex=128x128",
        "productCaption": "鉄道会社の社長となり、都市開発を行うシリーズ最新作。列車や建物の種類が大幅に増加し、老朽化や主力資源、街並の変化など、時代の変遷を味わえる。",
        "releaseDate": "2014年02月13日",
        "makerCode": "104988640",
        "makerName": "アートディンク",
        "makerNameKana": "アートデインク",
        "makerNameFormal": "株式会社アートディンク",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/562905/104988640/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/562905/104988640/",
        "itemCount": 68,
        "salesItemCount": 33,
        "usedExcludeCount": 36,
        "usedExcludeSalesItemCount": 20,
        "maxPrice": 10890,
        "salesMaxPrice": 10890,
        "usedExcludeMaxPrice": 10890,
        "usedExcludeSalesMaxPrice": 10890,
        "minPrice": 3880,
        "salesMinPrice": 4082,
        "usedExcludeMinPrice": 3880,
        "usedExcludeSalesMinPrice": 4930,
        "averagePrice": 5207,
        "reviewCount": 18,
        "reviewAverage": 4.67,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/673ba66b41abdc42e2c0be1091d58240/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/673ba66b41abdc42e2c0be1091d58240/review/",
        "rank": 2174,
        "rankTargetGenreId": "553848",
        "rankTargetProductCount": 4870,
        "genreId": "562905",
        "genreName": "その他",
        "ProductDetails": [
          {
            "detail": {
              "name": "フリガナ",
              "value": "エーレッシャデイコウスリーディー"
            }
          },
          {
            "detail": {
              "name": "プラットフォーム",
              "value": "3DS"
            }
          },
          {
            "detail": {
              "name": "ジャンル",
              "value": "シミュレーション"
            }
          },
          {
            "detail": {
              "name": "テイスト",
              "value": "経営・鉄道"
            }
          },
          {
            "detail": {
              "name": "型番",
              "value": "CTRPAALJ"
            }
          },
          {
            "detail": {
              "name": "その他",
              "value": "ダウンロードコンテンツ対応"
            }
          },
          {
            "detail": {
              "name": "CEROレーティング",
              "value": "A 全年齢対象"
            }
          },
          {
            "detail": {
              "name": "プレイ人数",
              "value": "1人"
            }
          },
          {
            "detail": {
              "name": "ディレクター",
              "value": "飯塚正樹"
            }
          }
        ]
      }
    }
  ],
  "GenreInformation": {
    "parent": [],
    "current": [],
    "children": []
  }
}
```

