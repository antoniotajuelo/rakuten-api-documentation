
### BooksBook/Search

#### Description

Gets up to 30 book items by title, author, publisher, size, ISBN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksBook/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
title<br>*Title* | string | Optional | Search for a book title.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
author<br>*Author* | string | Optional | Search for an author's name.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
publisherName<br>*Publisher name* | string | Optional | Search for a publisher.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
size<br>*Size* | integer | Optional | Search from the size of the books
isbn<br>*ISBN code* | string | Optional | Search for a ISBN code (book code).
booksGenreId<br>*Book genre ID* | string | Optional | Use it for narrow results to a specific book genre ID.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30
page<br>*Result page* | integer | Optional | An integer between 1 and 100
availability<br>*Availability* | integer | Optional | 
outOfStockFlag<br>*Out of Stock Flag* | integer | Optional | 
chirayomiFlag<br>*Chira Yomi Flag* | integer | Optional | 
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.
carrier<br>*Platform* | integer | Optional | 
genreInformationFlag<br>*Genre information flag* | integer | Optional | 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/BooksBook/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&hits=3
##### Response

```json
{
  "count": 872095,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 100,
  "Items": [
    {
      "Item": {
        "title": "【バーゲン本】イラスト刺しゅうの素敵",
        "titleKana": "イラストシシュウノステキ",
        "subTitle": "",
        "subTitleKana": "",
        "seriesName": "",
        "seriesNameKana": "",
        "contents": "",
        "author": "三林　よし子",
        "authorKana": "ミツバヤシ　ヨシコ",
        "publisherName": "（株）パッチワーク通信社",
        "size": "ムックその他",
        "isbn": "4528189418158",
        "itemCaption": "",
        "salesDate": "",
        "itemPrice": 561,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13340978/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/8158/4528189418158.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/8158/4528189418158.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/8158/4528189418158.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "1",
        "postageFlag": 0,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "001023"
      }
    },
    {
      "Item": {
        "title": "手帳 リングダイアリースリム（月間ブロック・レフト） （ウィークリー） H210×W118mm No.90 2016年",
        "titleKana": "90 リング ダイアリー スリム ゲッカン ブロック レフト",
        "subTitle": "",
        "subTitleKana": "",
        "seriesName": "",
        "seriesNameKana": "",
        "contents": "",
        "author": "",
        "authorKana": "",
        "publisherName": "高橋書店",
        "size": "ムックその他",
        "isbn": "9784471750909",
        "itemCaption": "",
        "salesDate": "2015年09月",
        "itemPrice": 1080,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13377485/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0909/9784471750909.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0909/9784471750909.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0909/9784471750909.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "6",
        "postageFlag": 0,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "001026"
      }
    },
    {
      "Item": {
        "title": "【バーゲン本】ビーズ刺しゅう基本ステッチー写真を見ながら学ぶ",
        "titleKana": "ビーズシシュウキホンステッチーシャシンヲミナガラマナブ",
        "subTitle": "",
        "subTitleKana": "",
        "seriesName": "レッスンシリーズ",
        "seriesNameKana": "レッスンシリーズ",
        "contents": "",
        "author": "小倉　ゆき子",
        "authorKana": "オグラ　ユキコ",
        "publisherName": "（株）パッチワーク通信社",
        "size": "ムックその他",
        "isbn": "4528189418134",
        "itemCaption": "",
        "salesDate": "",
        "itemPrice": 626,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13340976/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/8134/4528189418134.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/8134/4528189418134.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/8134/4528189418134.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "1",
        "postageFlag": 0,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "001023"
      }
    }
  ],
  "GenreInformation": []
}
```

