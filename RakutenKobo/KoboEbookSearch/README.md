
# Kobo/EbookSearch

## Description

Gets up to 30 Kobo items by keyword, title, author, publisher, item number or genre.
## Resource URL

https://app.rakuten.co.jp/services/api/Kobo/EbookSearch/20140811
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

keyword<br>*Keyword* | string | At least one is required | Search for keyword.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.

title<br>*Book title* | string | At least one is required | Search for book title.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.

author<br>*Author's name* | string | At least one is required | Search for author's name.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.

publisherName<br>*Publisher* | string | At least one is required | Search for publisher's name.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.

itemNumber<br>*Item Number* | string | At least one is required | Search for item number.

koboGenreId<br>*Kobo Genre ID* | string | At least one is required | ID for identifying the genre in Rakuten Kobo<br>(Please note that this ID is different from the Rakuten Ichiba genre ID)<br>Parent is KoboGenreId = 101 (e-book).<br>If you want to browse the Genre structure, please use the "Rakuten Kobo genre search API (Kobo/GenreSearch)".
<br>*Default Value:* <code>101</code>
language<br>*Language* | string | Optional | It is possible to specify the language of the e-book

hits<br>*How many results per page* | integer | Optional | Integer 1 to 30.
<br>*Default Value:* <code>30</code>
page<br>*Result page* | integer | Optional | Integer 1 to 100.
<br>*Default Value:* <code>1</code>
sort<br>*Sort* | string | Optional | ※ Please use UTF-8 encoded parameters.
<br>*Valid Values:*
* <code>standard</code> standard
* <code>+releaseDate</code> Release Date (old)
* <code>-releaseDate</code> Release Date (new)
* <code>+itemPrice</code> Cheap price
* <code>-itemPrice</code> high price
* <code>reviewCount</code> Number of reviews
* <code>reviewAverage</code> High rating average
<br>*Default Value:* <code>standard</code>
NGKeyword<br>*Negative Keywords* | string | Optional | Keywords that you want to exclude from search query.

field<br>*Search field* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> Broad search match
* <code>1</code> Exact search match
<br>*Default Value:* <code>1</code>
orFlag<br>*OR search flag* | integer | Optional | When multiple keywords are set it defaults for AND operator search, but you can switch to OR operator mode.
<br>*Valid Values:*
* <code>0</code> AND search
* <code>1</code> OR search
<br>*Default Value:* <code>0</code>
genreInformationFlag<br>*Genre information flag	* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> do not get the items of information for each genre
* <code>1</code> get the items of information for each genre
<br>*Default Value:* <code>0</code>
salesType<br>*Sales Type* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> Normal items
* <code>1</code> Pre-Orders
<br>*Default Value:* <code>ALL</code>
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

https://app.rakuten.co.jp/services/api/Kobo/EbookSearch/20140811?applicationId=REPLACE_WITH_YOUR_APP_ID&author=村上春樹&hits=3
### Response

```json
{
  "count": 12,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "pageCount": 4,
  "Items": [
    {
      "Item": {
        "title": "遠い太鼓",
        "titleKana": "トオイタイコ",
        "subTitle": "",
        "seriesName": "",
        "author": "村上春樹",
        "authorKana": "ムラカミハルキ",
        "publisherName": "講談社",
        "language": "JA",
        "salesDate": "2015年11月27日",
        "itemNumber": "4310000025842",
        "koboGenreId": "101901",
        "itemCaption": "ある朝目が覚めて、ふと耳を澄ませると、何処か遠くから太鼓の音が聞こえてきた。その音を聞いているうちに、僕はどうしても長い旅に出たくなったのだーー。40歳になろうとしていた著者は、ある思いに駆られて日本を後にし、ギリシャ･イタリアへ長い旅に出る。『ノルウェイの森』と『ダンス･ダンス･ダンス』を書き上げ、作家としての転換期となった、三年間の異国生活のスケッチブック。",
        "itemPrice": 864,
        "itemUrl": "http://books.rakuten.co.jp/rk/2f6c629361643a4d99584d1bcb2c9689",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/9a/6a/2f6c629361643a4d99584d1bcb2c9689.png?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/9a/6a/2f6c629361643a4d99584d1bcb2c9689.png?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/9a/6a/2f6c629361643a4d99584d1bcb2c9689.png?_ex=200x200",
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "salesType": 0
      }
    },
    {
      "Item": {
        "title": "やがて哀しき外国語",
        "titleKana": "ヤガテカナシキガイコクゴ",
        "subTitle": "",
        "seriesName": "",
        "author": "村上春樹",
        "authorKana": "ムラカミハルキ",
        "publisherName": "講談社",
        "language": "JA",
        "salesDate": "2015年11月27日",
        "itemNumber": "4310000025848",
        "koboGenreId": "101901",
        "itemCaption": "F･スコット･フィッツジェラルドの母校プリンストン大学に招かれ、アメリカでの暮らしが始まった。独自の大学村スノビズム、スティーブン･キング的アメリカ郊外事情、本場でジャズについて思うこと、フェミニズムをめぐる考察、海外で深く悩まされる床屋問題ーー。『国境の南、太陽の西』と『ねじまき鳥クロニクル』を執筆した二年あまりをつづった、十六通のプリンストン便り。",
        "itemPrice": 572,
        "itemUrl": "http://books.rakuten.co.jp/rk/ef6384b198243da89e93f75e2e7fc922",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/69/c0/ef6384b198243da89e93f75e2e7fc922.png?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/69/c0/ef6384b198243da89e93f75e2e7fc922.png?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/69/c0/ef6384b198243da89e93f75e2e7fc922.png?_ex=200x200",
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "salesType": 0
      }
    },
    {
      "Item": {
        "title": "色彩を持たない多崎つくると、彼の巡礼の年",
        "titleKana": "シキサイヲモタナイタザキツクルトカレノジュンレイノトシ",
        "subTitle": "",
        "seriesName": "",
        "author": "村上春樹",
        "authorKana": "ムラカミハルキ",
        "publisherName": "文藝春秋",
        "language": "JA",
        "salesDate": "2015年12月04日",
        "itemNumber": "4390000002827",
        "koboGenreId": "101901",
        "itemCaption": "多崎つくる、鉄道の駅をつくるのが仕事。名古屋での高校時代、四人の男女の親友と完璧な調和を成す関係を結んでいたが、大学時代のある日突然、四人から絶縁を申し渡された。何の理由も告げられずにーー。死の淵を一時さ迷い、漂うように生きてきたつくるは、新しい年上の恋人・沙羅に促され、あの時なにが起きたのか探り始めるのだった。全米第一位にも輝いたベストセラー！",
        "itemPrice": 780,
        "itemUrl": "http://books.rakuten.co.jp/rk/2b18ee45fa603300a20fe00f50c37110",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/0b/d3/2b18ee45fa603300a20fe00f50c37110.png?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/0b/d3/2b18ee45fa603300a20fe00f50c37110.png?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_gold/rakutenkobo-ebooks/imghb/0b/d3/2b18ee45fa603300a20fe00f50c37110.png?_ex=200x200",
        "reviewCount": 2,
        "reviewAverage": "3.5",
        "salesType": 0
      }
    }
  ],
  "GenreInformation": []
}
```

