
# BooksForeignBook/Search

## Description

Gets up to 30 foreign book items by title, author, publisher, ISBN or genre.
## Resource URL

https://app.rakuten.co.jp/services/api/BooksForeignBook/Search/20130522
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.<br>**Valid Values:**
title<br>*Title* | string | At least one is required | Search for a book title.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.<br>**Valid Values:**
author<br>*Author* | string | At least one is required | Search for an author's name.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.<br>**Valid Values:**
publisherName<br>*Publisher name* | string | At least one is required | Search for a publisher.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.<br>**Valid Values:**
isbn<br>*Book ISBN code* | string | At least one is required | Search for a ISBN code (book code).<br>**Valid Values:**
booksGenreId<br>*Book genre ID	* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 005 (Foreign Book) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.<br>**Valid Values:**<br>**Default Value:** <code>005</code>
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.<br>**Valid Values:**<br>**Default Value:** <code>30</code>
page<br>*Result page* | integer | Optional | An integer between 1 and 100.<br>**Valid Values:**<br>**Default Value:** <code>1</code>
availability<br>*Availability* | integer | Optional | **Valid Values:**<br><code>0</code> all items<br><code>1</code> In Stock<br><code>2</code> Usually ships in about 3 to 7 days<br><code>3</code> Usually ships in about 3 to 9 days<br><code>4</code> Manufacturer stock<br><code>5</code> Preorder<br><code>6</code> Check stock with manufacturer<br>**Default Value:** <code>0</code>
outOfStockFlag<br>*Out of Stock Flag	* | integer | Optional | **Valid Values:**<br><code>0</code> Do not include out of stock items.<br><code>1</code> Include out of stock items.<br>**Default Value:** <code>0</code>
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.<br>**Valid Values:**<br><code>standard</code> <br><code>sales</code> <br><code>+releaseDate</code> Release date (Ascending order)<br><code>-releaseDate</code> Release date (Descending order)<br><code>+itemPrice</code> Item price (Ascending order)<br><code>-itemPrice</code> Item price (Descending order)<br><code>reviewCount</code> <br><code>reviewAverage</code> <br>**Default Value:** <code>0</code>
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.<br>**Valid Values:**<br><code>0</code> All items<br><code>1</code> Limited Edition only<br>**Default Value:** <code>0</code>
carrier<br>*Platform* | integer | Optional | **Valid Values:**<br><code>0</code> PC<br><code>1</code> Mobile<br>**Default Value:** <code>0</code>
genreInformationFlag<br>*Genre information flag* | integer | Optional | **Valid Values:**<br><code>0</code> Do not get number of item in each genre.<br><code>1</code> Get number of item in each genre.<br>**Default Value:** <code>0</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.<br>**Valid Values:**
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.<br>**Valid Values:**
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code><br>**Valid Values:**
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/BooksForeignBook/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&author=cervantes&hits=3
### Response

```json
{
  "count": 62,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 21,
  "Items": [
    {
      "Item": {
        "title": "Gaby, Lost and Found",
        "titleKana": "",
        "japaneseTitle": "Gaby, Lost and Found",
        "author": "Angela Cervantes",
        "authorKana": "Angela Cervantes",
        "publisherName": "PERFECTION LEARNING CORP",
        "isbn": "9781680650211",
        "itemCaption": "",
        "salesDate": "2015年",
        "itemPrice": 2695,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13476669/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "4",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "005407002"
      }
    },
    {
      "Item": {
        "title": "Diccionario Practico del Estudiante",
        "titleKana": "",
        "japaneseTitle": "Diccionario Practico del Estudiante",
        "author": "Miguel De Cervantes",
        "authorKana": "Miguel De Cervantes",
        "publisherName": "REAL ACADEMIA ESPANOLA",
        "isbn": "9788430699537",
        "itemCaption": "",
        "salesDate": "2015年",
        "itemPrice": 2488,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13399589/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/9537/9788430699537.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/9537/9788430699537.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/9537/9788430699537.jpg?_ex=200x200",
        "availability": "4",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "005408004"
      }
    },
    {
      "Item": {
        "title": "Diccionario del Estudiante",
        "titleKana": "",
        "japaneseTitle": "Diccionario del Estudiante",
        "author": "Miguel De Cervantes",
        "authorKana": "Miguel De Cervantes",
        "publisherName": "TAURUS",
        "isbn": "9788430617494",
        "itemCaption": "",
        "salesDate": "2015年",
        "itemPrice": 6220,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13399587/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/7494/9788430617494.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/7494/9788430617494.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/7494/9788430617494.jpg?_ex=200x200",
        "availability": "4",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "005408004"
      }
    }
  ],
  "GenreInformation": []
}
```

