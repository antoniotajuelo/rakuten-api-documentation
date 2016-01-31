
### FavoriteBookmark/List

#### Description

Gets up to 40 favorite bookmarks from the user performing the API call.
#### Resource URL

https://app.rakuten.co.jp/services/api/FavoriteBookmark/List/20120627
#### Resource Information

* **Auth Type** OAuth
* **OAuth Scope** Gets up to 40 favorite bookmarks from the user performing the API call.
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
page<br>*Page number* | integer | Optional | Starting number of the page to get
hits<br>*Number of results* | integer | Optional | Items per page. Maximum: 40.
sort<br>*Sort* | string | Optional | * In the case of the same registration date and time and the same price, the order cannot be predicted.
ispublic<br>*Only get public items* | string | Optional | 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/FavoriteBookmark/List/20120627?access_token=REPLACE_WITH_THE_USER_ACCESS_TOKEN
##### Response

```json
{
  "summary": {
    "count": 2,
    "hits": 1,
    "pageCount": 2
  },
  "items": [
    {
      "item": {
        "bookmarkId": "4857547",
        "itemCode": "",
        "productId": "7e9f338152a7cf385b990611358ebd77",
        "shopName": "商品価格ナビ",
        "shopUrl": "http://product.rakuten.co.jp/",
        "itemName": "ねんどろいど チノ グッドスマイルカンパニー",
        "itemUrl": "http://product.rakuten.co.jp/product/-/7e9f338152a7cf385b990611358ebd77/",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/416/900/522/10010004580416900522_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/416/900/522/10010004580416900522_1.jpg?_ex=128x128",
        "reviewCount": 0,
        "reviewUrl": "",
        "pointRate": 0,
        "reviewAverage": "",
        "postageFlag": 99,
        "taxFlag": 0,
        "affiliateUrl": ""
      }
    }
  ]
}
```

