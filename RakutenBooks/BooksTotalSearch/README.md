
# BooksTotal/Search

## Description

Gets up to 30 media items by keywords, genre or ISBN/JAN.
## Resource URL

https://app.rakuten.co.jp/services/api/BooksTotal/Search/20130522
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
keyword<br>*Search keywords* | string | At least one is required | UTF-8 URL encoded string<br>The keyword parameter can have a maximum length of 128 single byte characters<br>The keyword parameter is delimited with single byte space characters. This defaults to an AND operation including all the keywords. To use OR instead set the orFlag to 1.<br>Each search keyword must be at least two single byte characters or one double byte character.<br>An exception is a minimum of two characters if the search keywords are using hiragana, katakana, or symbols.
booksGenreId<br>*Book genre ID* | string | At least one is required | Book ID to specify a book genre.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>**Default Value:** <code>000</code>
isbnjan<br>*ISBN/JAN code* | string | At least one is required | Use a 13 character code by removing all the hyphen symbols.<br>(*1) If ISBN/JAN code is specified, please do not set the search keywords and book genre ID parameters.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30<br>**Default Value:** <code>30</code>
page<br>*Result page* | integer | Optional | An integer between 1 and 100<br>**Default Value:** <code>1</code>
availability<br>*Availability* | integer | Optional | <br>*Valid Values:*<br><code>0</code> all items<br><code>1</code> In Stock<br><code>2</code> Usually ships in about 3 to 7 days<br><code>3</code> Usually ships in about 3 to 9 days<br><code>4</code> Manufacturer stock<br><code>5</code> Preorder<br><code>6</code> Check stock with manufacturer<br>**Default Value:** <code>0</code>
outOfStockFlag<br>*Out of Stock Flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Do not include out of stock items.<br><code>1</code> Include out of stock items.<br>**Default Value:** <code>0</code>
chirayomiFlag<br>*Chira Yomi Flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All items.<br><code>1</code> Only chirayomi (free preview) items.<br>**Default Value:** <code>0</code>
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.<br>*Valid Values:*<br><code>standard</code> <br><code>sales</code> <br><code>+releaseDate</code> Release date (Ascending order)<br><code>-releaseDate</code> Release date (Descending order)<br><code>+itemPrice</code> Item price (Ascending order)<br><code>-itemPrice</code> Item price (Descending order)<br><code>reviewCount</code> <br><code>reviewAverage</code> <br>**Default Value:** <code>standard</code>
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.<br>*Valid Values:*<br><code>0</code> All items<br><code>1</code> Limited Edition only<br>**Default Value:** <code>0</code>
field<br>*Search field* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Broad search (prefer more matches with the same keyword)<br><code>1</code> Restricted search (prefer fewer matches with the same keyword)<br>**Default Value:** <code>0</code>
carrier<br>*Platform* | integer | Optional | <br>*Valid Values:*<br><code>0</code> PC<br><code>1</code> Mobile<br>**Default Value:** <code>1</code>
orFlag<br>*OR search flag* | integer | Optional | Choose between AND searches and OR searches when there are multiple keywords.<br>*It isn't possible to use a complex search condition like "(A and B) or C".<br>*Valid Values:*<br><code>0</code> AND<br><code>1</code> OR<br>**Default Value:** <code>0</code>
NGKeyword<br>*Excluded keywords (*3)* | string | Optional | Words to exclude from search results<br>Strings encoded with UTF-8 URL encoding<br>Same format as keyword<br>(*3) This field can only be used if the search keywords field is set.
genreInformationFlag<br>*Genre information flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Do not get number of item in each genre.<br><code>1</code> Get number of item in each genre.<br>**Default Value:** <code>0</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>*Valid Values:*<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>*Valid Values:*<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/BooksTotal/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=ドン・キホーテ&hits=3
### Response

```json
{
  "count": 119,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 40,
  "Items": [
    {
      "Item": {
        "title": "ドン・キホーテ 1-2巻セット",
        "author": "行徒/河田雄志",
        "artistName": "",
        "publisherName": "新潮社",
        "label": "",
        "isbn": "2100010283771",
        "jan": "",
        "hardware": "",
        "os": "",
        "itemCaption": "",
        "salesDate": "2015年03月",
        "itemPrice": 1210,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13144177/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3771/2100010283771.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3771/2100010283771.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3771/2100010283771.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "1",
        "postageFlag": 0,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "001025"
      }
    },
    {
      "Item": {
        "title": "ドン・キホーテ（全6冊セット）",
        "author": "ミゲル・デ・セルバンテス・サアベドラ/牛島信明",
        "artistName": "",
        "publisherName": "岩波書店",
        "label": "",
        "isbn": "9784002010588",
        "jan": "",
        "hardware": "",
        "os": "",
        "itemCaption": "",
        "salesDate": "2001年07月",
        "itemPrice": 5875,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/1362072/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0588/9784002010588.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0588/9784002010588.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0588/9784002010588.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "1",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 3,
        "reviewAverage": "5.0",
        "booksGenreId": "001008022008"
      }
    },
    {
      "Item": {
        "title": "R.シュトラウス:交響詩≪ドン・キホーテ≫ 交響詩≪ティル・オイレンシュピーゲルの愉快ないたずら≫",
        "author": "",
        "artistName": "ヘルベルト・フォン・カラヤン/アントニオ・メネセス/ヴォルフラム・クリスト/リヒャルト・シュトラウス/ヘルベルト・フォン・カラヤン/アントニオ・メネセス",
        "publisherName": "",
        "label": "ユニバーサルミュージック クラシック",
        "isbn": "",
        "jan": "4988005753465",
        "hardware": "",
        "os": "",
        "itemCaption": "",
        "salesDate": "2013年03月20日",
        "itemPrice": 1572,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/12169413/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3465/4988005753465.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3465/4988005753465.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3465/4988005753465.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "1",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "002104002"
      }
    }
  ],
  "GenreInformation": []
}
```

