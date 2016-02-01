
# BooksCD/Search

## Description

Gets up to 30 CD items by title, artist, label, JAN or genre.
## Resource URL

https://app.rakuten.co.jp/services/api/BooksCD/Search/20130522
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

title<br>*Title* | string | At least one is required | Keywords to search from the title of the CD.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.

artistName<br>*Artist Name* | string | At least one is required | Keywords to search from the artist's or composer's name.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.

label<br>*Label* | string | At least one is required | Keywords to search from label releasing the items.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.

jan<br>*CD JAN code* | long | At least one is required | Search for a JAN code associated to a CD.

bookGenreId<br>*Book genre ID* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 002 (CD) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
<br>*Default Value:* <code>002</code>
hits<br>*How many results to display on each page	* | integer | Optional | An integer between 1 and 30.
<br>*Default Value:* <code>30</code>
page<br>*Result page	* | integer | Optional | An integer between 1 and 100.
<br>*Default Value:* <code>1</code>
availability<br>*Availability* | integer | Optional | 
<br>*Valid Values:*
<br><code>0</code> all items
<br><code>1</code> In Stock
<br><code>2</code> Usually ships in about 3 to 7 days
<br><code>3</code> Usually ships in about 3 to 9 days
<br><code>4</code> Manufacturer stock
<br><code>5</code> Preorder
<br><code>6</code> Check stock with manufacturer
<br>*Default Value:* <code>0</code>
outOfStockFlag<br>*Out of Stock Flag	* | integer | Optional | 
<br>*Valid Values:*
<br><code>0</code> Do not include out of stock items.
<br><code>1</code> Include out of stock items.
<br>*Default Value:* <code>0</code>
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
<br>*Valid Values:*
<br><code>standard</code> 
<br><code>sales</code> 
<br><code>+releaseDate</code> Release date (Ascending order)
<br><code>-releaseDate</code> Release date (Descending order)
<br><code>+itemPrice</code> Item price (Ascending order)
<br><code>-itemPrice</code> Item price (Descending order)
<br><code>reviewCount</code> 
<br><code>reviewAverage</code> 
<br>*Default Value:* <code>standard</code>
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.
<br>*Valid Values:*
<br><code>0</code> All items
<br><code>1</code> Limited Edition only
<br>*Default Value:* <code>0</code>
carrier<br>*Platform* | integer | Optional | 
<br>*Valid Values:*
<br><code>0</code> PC
<br><code>1</code> Mobile
<br>*Default Value:* <code>0</code>
genreInformationFlag<br>*Genre information flag* | integer | Optional | 
<br>*Valid Values:*
<br><code>0</code> Do not get number of item in each genre.
<br><code>1</code> Get number of item in each genre.
<br>*Default Value:* <code>0</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.

format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
<br>*Valid Values:*
<br><code>json</code> 
<br><code>xml</code> 
<br>*Default Value:* <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.

elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>

formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
<br>*Valid Values:*
<br><code>1</code> 
<br><code>2</code> 
<br>*Default Value:* <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/BooksCD/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&artistName=speed&hits=3
### Response

```json
{
  "count": 78,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 26,
  "Items": [
    {
      "Item": {
        "title": "【輸入盤】3RDシングル：スピード・オン",
        "titleKana": "",
        "artistName": "Speed (Korea)",
        "artistNameKana": "スピード",
        "label": "Interpark Int",
        "size": "0",
        "jan": "8809447080178",
        "makerCode": "INT0026",
        "itemCaption": "ボーイズ・グループSPEEDが最新シングル\"What U\"で約1年ぶりにカムバック！新メンバーを加えた新たなグループ編成で再びシーンに舞い戻る！\n\n＜収録内容＞\n1. What U\n2. Rose\n3. 贈り物のような一人（Baby U）\n4. Rose（Inst.）\n5. ギフトのような一人（Baby U）（Inst.）",
        "playList": "",
        "salesDate": "2015年06月19日",
        "itemPrice": 2043,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13282762/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0178/8809447080178.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0178/8809447080178.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0178/8809447080178.jpg?_ex=200x200",
        "availability": "1",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "002115001"
      }
    },
    {
      "Item": {
        "title": "Straight Shooter",
        "titleKana": "ストレート シューター",
        "artistName": "スピードトラップ",
        "artistNameKana": "スピードトラップ",
        "label": "(有)スピリチュアル・ビースト",
        "size": "1",
        "jan": "4571139013095",
        "makerCode": "IUCP-16226",
        "itemCaption": "",
        "playList": "ノー・グローリー・ファウンド###トーチズ・アブレイズ###ランニング・ランパント###アイズ・フォー・コンクエスト###サーヴ・ユア・マスターズ###ストレート・シューター###ヘヴィ・アーマー###サヴェージ・ザ・プレイ###アイ・ウォント・トゥ・コンカー・ザ・ワールド (日本盤ボーナス・トラック)",
        "salesDate": "2015年09月23日",
        "itemPrice": 2776,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13305613/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3095/4571139013095.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3095/4571139013095.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/3095/4571139013095.jpg?_ex=200x200",
        "availability": "1",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "002102002"
      }
    },
    {
      "Item": {
        "title": "【輸入盤】Furious 7 - Original Score",
        "titleKana": "Furious 7 - Original Score",
        "artistName": "ワイルド スピード Sky Mission",
        "artistNameKana": "Furious Seven ワイルドスピード スカイミッション スカイ ミッション ワイルドスピード7",
        "label": "Backlot Music",
        "size": "0",
        "jan": "0851147006024",
        "makerCode": "602",
        "itemCaption": "Disc1\n1 : Furious 7\n2 : Paratroopers\n3 : Awakening\n4 : Operation Ramsey\n5 : Battle of the Titans\n6 : Parting Ways\n7 : Mountain Hijack\n8 : Homecoming\n9 : Beast in a Cage\n10 : Homefront\n11 : Vow for Revenge\n12 : Party Crashers\n13 : The Three Towers\n14 : God's Eye\n15 : When Worlds Collide\n16 : Remembrance\n17 : Hobbs Is the Cavalry\n18 : Operation Carjack\n19 : A Completely Insane Plan\n20 : Letty and Dom\n21 : Heist in the Desert\n22 : No More Funerals\n23 : Hobbs vs Shaw\n24 : Connected\n25 : About to Get Real Serious up in Here\n26 : Family\n27 : One Last Stand\n28 : Farewell\nPowered by HMV",
        "playList": "",
        "salesDate": "2015年03月31日",
        "itemPrice": 2231,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13267684/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/6024/0851147006024.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/6024/0851147006024.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/6024/0851147006024.jpg?_ex=200x200",
        "availability": "1",
        "postageFlag": 1,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "002111003"
      }
    }
  ],
  "GenreInformation": []
}
```

