
### AuctionItemCode/Search

#### Description

Gets an auction item by auction item code.
#### Resource URL

https://app.rakuten.co.jp/services/api/AuctionItemCode/Search/20121010
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
itemCode<br>*Auction item code* | string | Required | In order to find this value, please use the Rakuten auction Product Search API.
carrier<br>*Platform* | integer | Optional | Whether to return information for PC or mobile.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/AuctionItemCode/Search/20121010?applicationId=REPLACE_WITH_YOUR_APP_ID&itemCode=a:10959536:10024189
##### Response

```json
{
  "carrier": "0",
  "Items": [
    {
      "Item": {
        "itemName": "★郵便切手の歩み切手シート★第3集★銘版・ＣＭ付き80円4連★",
        "catchcopy": "",
        "itemCode": "a:10959536:10024189",
        "itemPrice": 600,
        "minPrice": 600,
        "itemCaption": "1995.1.25.発行　3.3×4.5cm　状態：良  ＜送付方法＞特定記録郵便、ゆうパック郵便   ※時間外及び土・日・祝日の場合、当方からのご連絡は翌平日10：00〜18：00となります。 ※当方からの直接メールが迷惑ホルダーに流れてしまうケースがありますので、ご落札の際は受取設定（ドメイン解除）をお願いします。  ※ご入札の後、稀に「終了前の入札削除の申し込み」をする方がいますが、不適切者でない限り当方から削除することはありません。終了後、「落札者都合によるキャンセル」として削除しますので、軽率な仮押さえ・間違い入札は慎重にご熟慮下さい。自己責任となります。",
        "itemUrl": "http://auction.rakuten.co.jp/item/10959536/a/10024189/",
        "affiliateUrl": "",
        "imageFlag": "1",
        "smallImageUrl": "http://auction.thumbnail.image.rakuten.co.jp/@0_aucitem/image3/536/10959536/1205/img3600057636273.jpg?_ex=64x64",
        "mediumImageUrl": "http://auction.thumbnail.image.rakuten.co.jp/@0_aucitem/image3/536/10959536/1205/img3600057636273.jpg?_ex=128x128",
        "blowFlag": 0,
        "blowPrice": "",
        "resultFlag": 0,
        "bidCount": 0,
        "taxFlag": 2,
        "postageFlag": 1,
        "deliveryType": 0,
        "creditCardFlag": 1,
        "affiliateRate": "1.0",
        "startTime": "2015-12-05 17:00:00",
        "endTime": "2015-12-13 00:57:00",
        "searchwordcost": 0,
        "shopName": "markazuyo",
        "shopStatusFlag": "1",
        "auctionGenreId": "1130027830"
      }
    }
  ]
}
```

