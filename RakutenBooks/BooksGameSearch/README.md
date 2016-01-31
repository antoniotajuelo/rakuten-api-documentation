
### BooksGame/Search

#### Description

Gets up to 30 game items by title, hardware, maker, label, JAN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksGame/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
title<br>*Game Title* | string | At least one is required | Keywords to search from the game title.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
hardware<br>*Compatible Platforms (Hardware)* | string | At least one is required | Search for compatible platforms (hardware).<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
makerCode<br>*MPN (Manufacturer Part Number)* | string | At least one is required | Search for MPN (Manufacturer Part Number).<br>This string needs to be UTF-8 encoded.
label<br>*Publisher name* | string | At least one is required | Keywords to search from publisher releasing the items.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
jan<br>*Game JAN code* | long | At least one is required | Search for a game JAN code.
booksGenreId<br>*Book genre ID* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 006 (games) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.
page<br>*Result page* | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional | 
outOfStockFlag<br>*Out of Stock Flag* | integer | Optional | 
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.
carrier<br>*Platform* | integer | Optional | 
genreInformationFlag<br>*Genre information flag	* | integer | Optional | 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/BooksGame/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&title=mario&hits=3
##### Response

```json
{
  "count": 64,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 22,
  "Items": [
    {
      "Item": {
        "title": "マリオテニス ウルトラスマッシュ",
        "titleKana": "マリオテニス ウルトラスマッシュ",
        "hardware": "Wii U",
        "label": "任天堂",
        "jan": "4902370531992",
        "makerCode": "WUP-P-AVXJ",
        "itemCaption": "\n\nジャンプに、巨大に、amiiboに。\nみんなで遊べる 『マリオテニス』 の最新作。\n\nシンプルな操作で多彩なショットを打ち分け、誰でもラリーの楽しさを味わえる 『マリオテニス』 シリーズ。\n最新作となる『マリオテニス　ウルトラスマッシュ』では、ローカル対戦や協力、インターネット対戦はもちろんのこと、ジャンプショットや巨大化するメガバトル、amiiboの育成など、テニスを軸としたさまざまな遊びを追加しています。\n\n●ひとりでも、みんなでもシングルスやダブルスなど最大4人で遊べます。\nインターネット対戦にも対応。世界中のプレイヤーと気軽に対戦できます。\n\n\n\n\n\n\n\n●amiiboを育成「勝ち抜きチャレンジ×amiibo」では、amiiboを自分のパートナーとして一緒に試合ができます。\n\n\n\n●2つの新要素で遊びが広がる・ダイナミックな試合を展開できるジャンプショット\n・巨大化して試合を有利に進めるメガバトルモード\n\n\n\n\n\n©2015-2016 Nintendo / CAMELOT",
        "salesDate": "2016年01月28日",
        "itemPrice": 4568,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13478219/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1992/4902370531992.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1992/4902370531992.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1992/4902370531992.jpg?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "006511006004"
      }
    },
    {
      "Item": {
        "title": "『マリオ＆ルイージRPG ペーパーマリオMIX・ マリオカート7』 ダブルパック",
        "titleKana": "『マリオ＆ルイージRPG ペーパーマリオMIX・ マリオカート7』 ダブルパック",
        "hardware": "Nintendo 3DS",
        "label": "任天堂",
        "jan": "4902370531862",
        "makerCode": "CTR-P-AWBJ",
        "itemCaption": "『マリオ＆ルイージRPG ペーパーマリオMIX』と『マリオカート7』のお得なダブルパック\n\n©2015 Nintendo Developed by ALPHADREAM\n©2011 Nintendo",
        "salesDate": "2015年12月03日",
        "itemPrice": 7560,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13478216/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1862/4902370531862.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1862/4902370531862.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1862/4902370531862.jpg?_ex=200x200",
        "availability": "1",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "006508005002/006508006001"
      }
    },
    {
      "Item": {
        "title": "マリオ花札・黒",
        "titleKana": "スーパーマリオ ハナフダ",
        "hardware": "玩具",
        "label": "任天堂",
        "jan": "4902370531770",
        "makerCode": "KRT-Z-NMHK",
        "itemCaption": "全札オリジナル柄　遊び方説明書入り。\n\n\n\n© Nintendo",
        "salesDate": "2015年11月20日",
        "itemPrice": 2430,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13425877/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1770/4902370531770.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1770/4902370531770.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1770/4902370531770.jpg?_ex=200x200",
        "availability": "1",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 1,
        "reviewAverage": "5.0",
        "booksGenreId": "006510006001"
      }
    }
  ],
  "GenreInformation": []
}
```

