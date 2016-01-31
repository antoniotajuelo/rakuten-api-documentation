
### BooksMagazine/Search

#### Description

Gets up to 30 magazine items by title, author, publisher, ISBN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksMagazine/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
title<br>*Title* | string | At least one is required | Search for a magazine title.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
publisherName<br>*Publisher name	* | string | At least one is required | Search for a publisher.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
jan<br>*Magazine JAN code* | long | At least one is required | Search for a magazine JAN code.
booksGenreId<br>*Book genre ID	* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 007 (Magazines) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page	* | integer | Optional | An integer between 1 and 30.
page<br>*Result page	* | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional | 
outOfStockFlag<br>*Out of Stock Flag	* | integer | Optional | 
chirayomiFlag<br>*Chira Yomi Flag	* | integer | Optional | 
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

https://app.rakuten.co.jp/services/api/BooksMagazine/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&title=vivi&hits=3
##### Response

```json
{
  "count": 2,
  "page": 1,
  "first": 1,
  "last": 2,
  "hits": 2,
  "carrier": 0,
  "pageCount": 1,
  "Items": [
    {
      "Item": {
        "title": "ViVi (ヴィヴィ) 2016年 02月号 [雑誌]",
        "titleKana": "ヴィヴィ",
        "publisherName": "講談社",
        "jan": "4910013790262",
        "itemCaption": "活動的な若い女性の為の総合ファッション誌",
        "salesDate": "2015年12月22日",
        "cycle": "月刊",
        "itemPrice": 669,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13515055/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "5",
        "postageFlag": 0,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "007606003"
      }
    },
    {
      "Item": {
        "title": "ViVi (ヴィヴィ) 2016年 01月号 [雑誌]",
        "titleKana": "ヴィヴィ",
        "publisherName": "講談社",
        "jan": "4910013790163",
        "itemCaption": "活動的な若い女性の為の総合ファッション誌\n※定期購読なら全品ポイント3倍！ViVi(ヴィヴィ） 送料無料1冊価格：670円（別ページに移動します) ※価格は変更される場合がございます。■ローラ 超ロングインタビュー! 〜新たなる朝を迎えて〜\n■MIU MIU 新作の靴とバッグにドキッ!!\n■“インスタ映え”が絶対!!\n毎日がイベントな冬が来た!!\nPART 1 マギーのモテピンク\nPART 2 ViViモデルズの「○○会」\nPART 3 #イベント命の冬コーデ!!\nPART 4 アリサの毎日イベントな着回し30days \nPART 5 おちゃめ小物。\nPART 6 my BEST パーティスタイル!!\n■デニム! モノトーン! ときどきファー。\nマギーのシンプルしか考えられない、冬。\n■この時期になって確定しました〜!!\n今すぐ買っとけ冬HIT50!\n■憧れのオトナシンプル\n中村アンの恋する冬ニット\n■ガウンコート、チェスターコート、ロングチェスターコート\n3大コートで着回し大作戦!!\n■レイナのXmasおねだりジュエリー\n■まゆーんの、マフラーぐるぐるとヘアのカンケイ。\n■NEWスカートでコーデで変わる!!\n■スタイリスト競演!\n冬コーデ問題解決塾!!\n【BEAUTY】\n■“さりげにオシャレ”なイベント対応ヘアアレンジ\n\n■イガリさんの妄想イベントLOVEメイク\n■ViVi認定 ベストコスメ 2015 \n■ALL \\1500以下! \n本当に使えるコスパコスメ大賞\n■2015年みんながやった&やりたい!\n美容なうネクRanking \n■クリスマスまでにLOVEボディ\nViVi的カウントダウンDIET!\n【OTHERS】\n■Christmas IDEA TIPS \nPART 1 ALL\\15000以下! おしゃれXmasギフト\nPART 2 失敗なしのパーティレシピ\n■今年の国宝級イケメン&次くる新星なうネク!!\n■クリスマスまでに彼氏をつくる30日のドリル\n■カズニョロ&ViViっ子軍団のポピポピお悩み相談室\n■tokyo boy cam＿41 吉沢 亮\n■綾野 剛・坂口健太郎・山□賢人・志尊 淳\n■2015年12月1日、ついにマギーのキレイのヒミツが解き明かされる!!\n■GO! GO! TAIWAN ローラも行ったよ最旬台湾 発売!",
        "salesDate": "2015年11月21日",
        "cycle": "月刊",
        "itemPrice": 669,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13470907/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0163/4910013790163.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0163/4910013790163.jpg?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0163/4910013790163.jpg?_ex=200x200",
        "chirayomiUrl": "",
        "availability": "1",
        "postageFlag": 0,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "007606003"
      }
    }
  ],
  "GenreInformation": []
}
```

