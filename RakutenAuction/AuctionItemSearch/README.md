
# AuctionItem/Search

## Description

Gets up to 30 auction items by keyword or auction genre id.
## Resource URL

https://app.rakuten.co.jp/services/api/AuctionItem/Search/20130110
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
keyword<br>*Search keywords* | string | At least one is required | UTF-8 string.<br>The entire search keyword must be specified within 128 characters.<br>Search keywords can be separated by a space, by default, it will be the AND conditions (search for those that contain all of the keyword). If you want to use OR conditions (search for those that contain any of the keyword), please set the orFlag to 1.<br>Each search keywords must be specified in the two characters or full-width one or more characters.<br>As an exception, it must be specified in two or more characters in the case of the hiragana and katakana and symbols each search keyword.
auctionGenreId<br>*Auction genre ID* | long | At least one is required | ID for identifying the genre in Rakuten auction.<br>If you want to get the genre ID from the genre name, please use the "Rakuten auction genre search API".<br>Parent genre ID is <code>0</code>.
hits<br>*How many results per page* | integer | Optional | Integer from 1 to 30.
page<br>*Result page* | integer | Optional | Integer from 1 to 100.
minItemPrice<br>*Minimum current price* | long | Optional | Integer 0 or greater.
maxItemPrice<br>*Maximum current price* | long | Optional | An integer of 0 or more.<br>maxItemPrice must be greater than minItemPrice.
sort<br>*Sort* | string | Optional | ※ You need to be URL encoded in UTF-8.
blowFlag<br>*Immediate purchase flag* | integer | Optional | ※ Immediate purchase items can be purchased immediately, without needing to wait for the auction time to finish.
minBlowPrice<br>*Minimum immediate bid price* | long | Optional | An integer equals to 0 or greater
maxBlowPrice<br>*Maximum immediate bid price* | long | Optional | An integer equals to 0 or greater.<br><code>maxBlowPrice</code> must be greter than <code>minBlowPrice</code>.
itemType<br>*Item Type* | integer | Optional | You can search for multiple types using a comma-separated list.<br>Example: <code>0,1,2</code>
newFlag<br>*Item condition flag* | integer | Optional | 
y1startFlag<br>*¥1 start flag* | integer | Optional | 
anonymityFlag<br>*Anonymous delivery corresponding flag* | integer | Optional | 
postageFreeFlag	<br>*Free shipping flag* | integer | Optional | 
closedFlag<br>*Closed exclusion flag* | integer | Optional | 
bidStatus<br>*Bid status* | integer | Optional | 
field<br>*Search field* | integer | Optional | 
carrier<br>*Platform* | integer | Optional | Whether to return information to be displayed on PC or mobile.
imageFlag<br>*Product Image Available flag* | integer | Optional | 
orFlag<br>*OR Search flag* | integer | Optional | When multiple keywords are entered, you can choose between doing an AND search or an OR search.<br>※ However, complex search conditions cannot be used, such as (A OR B) AND C.
NGKeyword<br>*Negative Keywords* | string | Optional | Keywords to exclude from search results.<br>UTF-8 encoded string.<br>Same format as the keyword parameter.
noticeIcon<br>*Notice Icon* | string | Optional | You can select multiple options using a comma-separated list.<br>Example: <code>0,1,2</code>
genreInformationFlag<br>*Genre information flag	* | integer | Optional | 
autoPriceDownFlag<br>*Auto Price Down Flag* | integer | Optional | 
priceDownExecFlag<br>*Price cut flag* | integer | Optional | 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/AuctionItem/Search/20130110?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=郵便切手&hits=3
### Response

```json
{
  "count": 137,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 46,
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
        "auctionGenreId": "1130027830",
        "noticeIcon": "0",
        "noticeBgColor": "0",
        "noticeLargeChar": "0"
      }
    },
    {
      "Item": {
        "itemName": "切手「西海国立公園郵便切手」1956年【新古品】0235【質屋出店】",
        "catchcopy": "",
        "itemCode": "a:11427521:10080210",
        "itemPrice": 6500,
        "minPrice": 6500,
        "itemCaption": "西海国立公園郵便切手シート　1956年",
        "itemUrl": "http://auction.rakuten.co.jp/item/11427521/a/10080210/",
        "affiliateUrl": "",
        "imageFlag": "1",
        "smallImageUrl": "http://auction.thumbnail.image.rakuten.co.jp/@0_aucitem/image3/521/11427521/1107/img9680617854978.jpg?_ex=64x64",
        "mediumImageUrl": "http://auction.thumbnail.image.rakuten.co.jp/@0_aucitem/image3/521/11427521/1107/img9680617854978.jpg?_ex=128x128",
        "blowFlag": 1,
        "blowPrice": "6500",
        "resultFlag": 0,
        "bidCount": 0,
        "taxFlag": 0,
        "postageFlag": 1,
        "deliveryType": 0,
        "creditCardFlag": 1,
        "affiliateRate": "1.0",
        "startTime": "2015-12-09 11:15:00",
        "endTime": "2015-12-13 11:15:00",
        "searchwordcost": 0,
        "shopName": "赤羽 フジヤ質店【質屋出店】",
        "shopStatusFlag": "3",
        "auctionGenreId": "1130027830",
        "noticeIcon": "0",
        "noticeBgColor": "0",
        "noticeLargeChar": "0"
      }
    },
    {
      "Item": {
        "itemName": "お年玉郵便切手(昭和30/33/35/36/40/41年他/0674【質屋出店】",
        "catchcopy": "",
        "itemCode": "a:11427521:10076592",
        "itemPrice": 9800,
        "minPrice": 9800,
        "itemCaption": "【値下げお買い得品！！】お年玉郵便切手(昭和30/33/35/36/40/41/42/43年【新古品】コレクション放出品です程度ABクラス/ 101148-53",
        "itemUrl": "http://auction.rakuten.co.jp/item/11427521/a/10076592/",
        "affiliateUrl": "",
        "imageFlag": "1",
        "smallImageUrl": "http://auction.thumbnail.image.rakuten.co.jp/@0_aucitem/image2/521/11427521/1018/img785047362967.jpg?_ex=64x64",
        "mediumImageUrl": "http://auction.thumbnail.image.rakuten.co.jp/@0_aucitem/image2/521/11427521/1018/img785047362967.jpg?_ex=128x128",
        "blowFlag": 1,
        "blowPrice": "9800",
        "resultFlag": 0,
        "bidCount": 0,
        "taxFlag": 0,
        "postageFlag": 1,
        "deliveryType": 0,
        "creditCardFlag": 1,
        "affiliateRate": "1.0",
        "startTime": "2015-12-09 11:24:00",
        "endTime": "2015-12-13 11:24:00",
        "searchwordcost": 0,
        "shopName": "赤羽 フジヤ質店【質屋出店】",
        "shopStatusFlag": "3",
        "auctionGenreId": "1130027830",
        "noticeIcon": "0",
        "noticeBgColor": "0",
        "noticeLargeChar": "0"
      }
    }
  ],
  "GenreInformation": []
}
```

