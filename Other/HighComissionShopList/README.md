
# HighComissionShop/List

## Description

Gets up to 30 Rakuten Ichiba shops offering an affiliate commission of 1.1 or higher.
## Resource URL

https://app.rakuten.co.jp/services/api/HighCommissionShop/List/20131205
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

hits<br>*How many results to display on each page* | integer | Optional | Integer 1 to 30.
<br>*Default Value:* <code>30</code>
page<br>*Page number* | integer | Optional | Integer 1 or more.
<br>*Default Value:* <code>1</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.

format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
<br>*Valid Values:*
* <code>json</code> 
* <code>xml</code> 
<br>*Default Value:* <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.

elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>

formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
<br>*Valid Values:*
* <code>1</code> 
* <code>2</code> 
<br>*Default Value:* <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/HighCommissionShop/List/20131205?applicationId=REPLACE_WITH_YOUR_APP_ID&hits=3
### Response

```json
{
  "count": 4339,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 100,
  "startApplyDate": "2015/12/15",
  "Shops": [
    {
      "Shop": {
        "shopName": "GLENCHECK",
        "shopCode": "glencheck",
        "shopUrl": "http://www.rakuten.co.jp/glencheck/",
        "shopPR": "海外各国から素材、機能性、そしてスタイリッシュさにこだわりぬいた逸品をご紹介。是非にお手にとって頂きたい商品ばかりです。革製品、アパレル、雑貨小物などなどラインナップも豊富。革小物へはお名入れ無料でギフトにも大好評です！！",
        "genreId": "216131",
        "genreName": "バッグ・小物・ブランド雑貨",
        "affiliateRateS": "10.0",
        "affiliateRateA": "10.0",
        "affiliateRateB": "10.0",
        "affiliateRateC": "10.0",
        "affiliateRateD": "10.0",
        "commissionType": "1",
        "affiliateUrl": null
      }
    },
    {
      "Shop": {
        "shopName": "JURER　DEUX＆THE　GRAND　SELECT",
        "shopCode": "jurer",
        "shopUrl": "http://www.rakuten.co.jp/jurer/",
        "shopPR": "1500点ものオリジナルのアクセサリーを心を込めて届けます。当ショップのアクセサリーならご購入後も万全のアフターフォローで安心のサービスです。",
        "genreId": "216129",
        "genreName": "ジュエリー・アクセサリー",
        "affiliateRateS": "8.0",
        "affiliateRateA": "2.0",
        "affiliateRateB": "2.0",
        "affiliateRateC": "2.0",
        "affiliateRateD": "2.0",
        "commissionType": "1",
        "affiliateUrl": null
      }
    },
    {
      "Shop": {
        "shopName": "韓国世界のグルメ＠キムチでやせる",
        "shopCode": "rabbit",
        "shopUrl": "http://www.rakuten.co.jp/rabbit/",
        "shopPR": "2012年に14周年を迎えた当店。老舗店である事と、ショップオブザイヤーのグランプリ受賞歴が、お客様に安心感を与え高い購入率を誇ります。楽天グルメ大賞2011を受賞した「韓国冷麺」を筆頭に、品揃えもバツグンです。どうぞご紹介よろしくお願いいたします。",
        "genreId": "100227",
        "genreName": "食品",
        "affiliateRateS": "10.5",
        "affiliateRateA": "10.5",
        "affiliateRateB": "10.5",
        "affiliateRateC": "10.5",
        "affiliateRateD": "10.5",
        "commissionType": "2",
        "affiliateUrl": null
      }
    }
  ]
}
```

