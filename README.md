# Rakuten API Documentation

Please check original for extra features: https://rakuten-api-documentation.antoniotajuelo.com/

## Rakuten Ichiba

![Rakuten Ichiba](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-ichiba.png)
* **Name** Rakuten Ichiba
* **URL** http://www.rakuten.co.jp/
* **Description** Rakuten's e-commerce platform.

### IchibaItem/Search

#### Description

Gets up to 30 items by keywords, shop, shop item code or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/IchibaItem/Search/20140222
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
keyword<br>*Search keywords* | string | At least one is required | UTF-8 URL encoded string<br>The keyword parameter can have a maximum length of 128 single byte characters<br>The keyword parameter is delimited with single byte space characters. This defaults to an AND operation including all the keywords. To use OR instead set the orFlag to 1.<br>Each search keyword must be at least two single byte characters or one double byte character.<br>An exception is a minimum of two characters if the search keywords are using hiragana, katakana, or symbols.
shopCode<br>*Shop code* | string | At least one is required | The portion of the shop URL listed as <code>xyz</code>: <code>http://www.rakuten.co.jp/xyz</code>
itemCode<br>*Item code* | string | At least one is required | Included in the output parameters of the Item Search, Item Ranking, and Bookmark APIs. <br>Please set a value in the form of <code>shop:1234</code>.
genreId<br>*Genre ID* | long | At least one is required | ID to specify a genre in Rakuten Ichiba<br>Please use the Rakuten Ichiba Genre Search API 2 to look up genre names and genre relations.
tagId<br>*Tag ID* | long | Optional | Comma separated (maximum 10 IDs)<br>ID to specify a tag in Rakuten Ichiba.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30
page<br>*Result page* | integer | Optional | An integer between 1 and 100
sort<br>*Sort* | string | Optional | UTF-8 URL encoding is required.
minPrice<br>*Minimum price* | long | Optional | An integer greater than 0 and less than 999,999,999
maxPrice<br>*Maximum price* | long | Optional | An integer greater than 0 and less than 999,999,999<br><code>maxPrice</code> must be greater than <code>minPrice</code>.
availability<br>*Availability* | integer | Optional |
field<br>*Search field* | integer | Optional |
carrier<br>*Platform* | integer | Optional | Choose the target platform for type of information to return: PC, mobile, or smartphone
imageFlag<br>*Has image flag* | integer | Optional |
orFlag<br>*OR search flag* | integer | Optional | Choose between AND searches and OR searches when there are multiple keywords. <br>*It isn't possible to use a complex search condition like "(A and B) or C".
NGKeyword<br>*Excluded keywords* | string | Optional | Words to exclude from search results<br>Strings encoded with UTF-8 URL encoding<br>Same format as keyword
purchaseType<br>*Purchase type* | integer | Optional | Narrow search by purchase type
shipOverseasFlag<br>*Overseas shipping flag* | integer | Optional |
shipOverseasArea<br>*Overseas shipping area* | string | Optional | It is possible to restrict searches based on delivery areas. <br>Check the overseas delivery area codes<br>*shipOverseasFlag must be 1
asurakuFlag<br>*Asuraku flag* | integer | Optional |
asurakuArea<br>*Asuraku area* | integer | Optional | It is possible to restrict searches based on delivery areas.<br>Check the Asuraku delivery area codes<br>*asurakuFlag must be 1
pointRateFlag<br>*Point multiplier flag* | integer | Optional | 0: All products<br>1: Only items with point multipliers
pointRate<br>*Point multiplier* | integer | Optional | An integer from 2 to 10 (e.g. 5 means points will be multiplied by five) <br>*pointRateFlag must be 1
postageFlag<br>*Postage flag* | integer | Optional |
creditCardFlag<br>*Credit card flag* | integer | Optional |
giftFlag<br>*Giftwrap flag* | integer | Optional |
hasReviewFlag<br>*Has review flag* | integer | Optional |
maxAffiliateRate<br>*Maximum affiliate rate * | float | Optional | A number from 1.0 to 99.9 (e.g. 5.0 for products with an affiliate rate up to 5%).<br>Don't show if the affiliate rate is higher than specified.<br>Up to one decimal place can be specified.
minAffiliateRate<br>*Minimum affiliate rate* | float | Optional | A number from 1.0 to 99.9 (e.g. 5.0 for products with an affiliate rate above 5%).<br>Don't show if the affiliate rate is lower than specified.<br>Up to one decimal place can be specified.<br>Specify an affiliate rate lower than the maximum rate.
hasMovieFlag<br>*Has movie flag* | integer | Optional |
pamphletFlag<br>*Pamphlet flag* | integer | Optional |
appointDeliveryDateFlag<br>*Specify delivery date flag* | integer | Optional |
elements<br>*Output elements* | string | Optional | Comma separated list.<br>When you specify this parameter, only those elements will be returned in the response.<br>Example: <code>elements=reviewCount,reviewAverage</code>
genreInformationFlag<br>*Genre information flag* | integer | Optional |
tagInformationFlag<br>*Tag information flag* | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/IchibaItem/Search/20140222?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=すし&hits=3
##### Response

```json
{
  "count": 25422,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 100,
  "Items": [
    {
      "Item": {
        "itemName": "【レビュー特典付き】【直営店】WOODYPUDDY はじめてのおままごと おすしセット【寿司 キッチン セット 木のおもちゃ 木のおままごと 木のままごと ウッディプッディ 知育玩具 送料無料】◎",
        "catchcopy": "【レビュー特典付き】【プレゼント ギフト 出産祝い 内祝い マグネット ままごとセット あす楽 おままごと】",
        "itemCode": "woodypuddy:10001478",
        "itemPrice": 6210,
        "itemCaption": "ラッピングのご希望はこちらからお選びください。熨斗のご希望はこちらからお選びください。※熨斗とリボンの併用については、熨斗にはリボンの意味があり、熨斗掛する場合は、同時にリボンを付けないことが一般的となっております。その為、熨斗のしきたり優先のため、熨斗とリボンの併用は出来かねますことを予めご了承くださいませ。【セット内容】（16アイテム）シャリX5、まぐろ、サーモン、タコ、エビ、玉子焼き、納豆、いくら、ぐんかん巻きx2、巻きずし、わさび、ガリX3、すしげた、しょうゆさし、しょうゆ皿、箸、印刷物2枚【サイズ】(mm)シャリ 50x25xH25まぐろ 60x28x9サーモン 60x28x9タコ 60x28x9エビ 77x35x9玉子焼き 64x30x10納豆 長さ13いくら 長さ16太巻き 伸ばすと138x6わさび 直径25xH20すし下駄 23x15xH20しょうゆさし 直径38xH55小皿 直径85x厚み5箸 直径9x長さ15軍艦 56x31xH29ガリ 直径15x厚み3EVAシール、印刷物2枚 【メーカー】WOODY PUDDY【オススメ】3歳くらい〜【素材】天然木（ブナ、イジュ、パイン）、ブナシート、合板、MDF、磁石、綿 　※素材は、インドネシア、中国、ドイツ、ニュージーランドなど複数産地【包装】化粧箱【重　量】0.81kg【生産国】中国【備考】2014/11/5　楽天リアルタイムランキング内容物以外は別売です【キーワード】 木のおもちゃ 木製おままごと　ままごとセット・表記寸法より多少の誤差が生じる場合もございます。・製造時期によって、色やデザイン、パッケージなど画像と多少異なる場合があります。 「関連ワード」 誕生日 ギフト プレゼント 贈り物 祝い オモチャ 玩具 知育玩具 入園祝い 出産祝い ままごとセット おままごとセット キッチンセット 知育 おかたづけギフト対応寿司 キッチン セット 木のおもちゃ 木のおままごと 木のままごと 木製 子供 キッズ 3歳 ウッディプッディ 知育玩具 送料無料 野菜 マグネット 食材少し長いですが、この商品が出来るまでをお伝えさせてください",
        "itemUrl": "http://item.rakuten.co.jp/woodypuddy/g05-1155/",
        "affiliateUrl": "",
        "shopAffiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/woodypuddy/cabinet/omamagoto/osushi/imgrc0061970650.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/woodypuddy/cabinet/omamagoto/osushi/imgrc0061970650.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 1,
        "shipOverseasArea": "ワールドワイド",
        "asurakuFlag": 1,
        "asurakuClosingTime": "12:00",
        "asurakuArea": "東京都/神奈川県/富山県/石川県/福井県/山梨県/長野県/岐阜県/静岡県/愛知県/三重県/滋賀県/京都府/大阪府/兵庫県/奈良県/和歌山県/鳥取県/島根県/岡山県/広島県/山口県/徳島県/香川県/愛媛県/高知県/福岡県",
        "affiliateRate": 5,
        "startTime": "",
        "endTime": "",
        "reviewCount": 90,
        "reviewAverage": 4.63,
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "giftFlag": 1,
        "shopName": "木のおもちゃ ままごと WOODYPUDDY",
        "shopCode": "woodypuddy",
        "shopUrl": "http://www.rakuten.co.jp/woodypuddy/",
        "genreId": "205275",
        "tagIds": []
      }
    },
    {
      "Item": {
        "itemName": "【ご贈答に最適】高知県馬路村「馬路すしの素」360m4本セット",
        "catchcopy": "大人気の馬路村のすし酢です。ご飯に合わせるだけですし飯が！",
        "itemCode": "shop-keyya:10002028",
        "itemPrice": 2392,
        "itemCaption": "馬路すしの素360m4本セット",
        "itemUrl": "http://item.rakuten.co.jp/shop-keyya/10002028/",
        "affiliateUrl": "",
        "shopAffiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/shop-keyya/cabinet/00899689/imgrc0069718957.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/shop-keyya/cabinet/00899689/imgrc0069718957.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 1,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": 1,
        "startTime": "",
        "endTime": "",
        "reviewCount": 0,
        "reviewAverage": 0,
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "giftFlag": 0,
        "shopName": "SHOP　KEYYA（しょっぷ　きいや）",
        "shopCode": "shop-keyya",
        "shopUrl": "http://www.rakuten.co.jp/shop-keyya/",
        "genreId": "507738",
        "tagIds": []
      }
    },
    {
      "Item": {
        "itemName": "すしThe　SUSHI　recipe　book [ 谷あつこ ]",
        "catchcopy": "【楽天ブックスならいつでも送料無料】",
        "itemCode": "book:13972678",
        "itemPrice": 1080,
        "itemCaption": "うちで作ろううちで食べようおうちSUSHI 谷あつこ 成瀬すみれ 成美堂出版発行年月：2010年10月 ページ数：107p サイズ：単行本 ISBN：9784415309347 谷あつこ（タニアツコ）食プランナー。料理雑誌やラジオ番組などで、食や栄養、健康をテーマにライター・エディターとして活動したのち、at　food設立。食コンサルティングや商品開発のほか、食文化セミナーや雑誌、書籍等で「食べ手」と「つくり手」を結ぶ企画提案を行っている成瀬すみれ（ナルセスミレ）料理研究家。料理研究家鈴木登紀子さんの助手を務めたのち、自宅で料理教室を主宰。雑誌や講習会などでも料理提案を行っている。季節感あふれる伝統的な日本料理の知識や技術をベースに、家庭料理に気軽にいかす調理法を基礎からていねいに教えている（本データはこの書籍が刊行された当時に掲載されていたものです） 押す／家ずしの基本／包む／巻く／詰める／混ぜる／外ずしの知識 本 美容・暮らし・健康・料理 料理 和食・おかず",
        "itemUrl": "http://item.rakuten.co.jp/book/6774685/",
        "affiliateUrl": "",
        "shopAffiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/9347/9784415309347.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/9347/9784415309347.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 1,
        "asurakuClosingTime": "12:00",
        "asurakuArea": "群馬県/埼玉県/千葉県/東京都/神奈川県/新潟県/富山県/石川県/福井県/山梨県/長野県/岐阜県/静岡県/愛知県/三重県/滋賀県/京都府/大阪府/兵庫県/奈良県/和歌山県/茨城県/栃木県",
        "affiliateRate": 1,
        "startTime": "",
        "endTime": "",
        "reviewCount": 4,
        "reviewAverage": 4.25,
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "giftFlag": 0,
        "shopName": "楽天ブックス",
        "shopCode": "book",
        "shopUrl": "http://www.rakuten.co.jp/book/",
        "genreId": "208792",
        "tagIds": []
      }
    }
  ],
  "GenreInformation": [],
  "TagInformation": []
}
```


### IchibaGenre/Search

#### Description

Gets a genre's attributes, tag groups, children genres, brother genres and ancestor genres by genre id.
#### Resource URL

https://app.rakuten.co.jp/services/api/IchibaGenre/Search/20120723
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
genreId<br>*Genre ID* | integer | Required | Use genreId=0 to search from the genre root
genrePath<br>*Genre path* | integer | Optional | 0: Exclude ancester genres <br>1: Display ancester genres <br>Ancestor genres are a set of genres in the upper levels (parent, grandparent, etc.)
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/IchibaGenre/Search/20120723?applicationId=REPLACE_WITH_YOUR_APP_ID&genreId=101164
##### Response

```json
{
  "parents": [],
  "current": {
    "genreId": 101164,
    "genreName": "おもちゃ・ホビー・ゲーム",
    "genreLevel": 1
  },
  "children": [
    {
      "child": {
        "genreId": 101189,
        "genreName": "おもちゃ",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 112203,
        "genreName": "フィギュア",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 101165,
        "genreName": "趣味・コレクション",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 101205,
        "genreName": "テレビゲーム",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 213731,
        "genreName": "パーティー・イベント用品・販促品",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 112132,
        "genreName": "占い・開運・風水・パワーストーン",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 101222,
        "genreName": "アート・美術品・骨董品・民芸品",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 206324,
        "genreName": "囲碁・将棋・麻雀・チェス",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "genreId": 112928,
        "genreName": "その他",
        "genreLevel": 2
      }
    }
  ]
}
```


### IchibaTag/Search

#### Description

Gets up to 10 tags and their tag group by tag id.
#### Resource URL

https://app.rakuten.co.jp/services/api/IchibaTag/Search/20140222
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
tagId<br>*Tag ID* | integer | Required | Comma-separated list of up to 10 tag IDs.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/IchibaTag/Search/20140222?applicationId=REPLACE_WITH_YOUR_APP_ID&tagId=1000579,1000943
##### Response

```json
{
  "tagGroups": [
    {
      "tagGroup": {
        "tagGroupName": "ブランド",
        "tagGroupId": 1000094,
        "tags": [
          {
            "tag": {
              "tagId": 1000579,
              "tagName": "ビルケンシュトック",
              "parentTagId": 0
            }
          }
        ]
      }
    },
    {
      "tagGroup": {
        "tagGroupName": "靴のスタイル",
        "tagGroupId": 1000114,
        "tags": [
          {
            "tag": {
              "tagId": 1000943,
              "tagName": "カジュアル",
              "parentTagId": 0
            }
          }
        ]
      }
    }
  ]
}
```


### IchibaItem/Ranking

#### Description

Gets up to 30 best seller items from all items, items from a specific genre or popular items among an age and gender demographic group.
#### Resource URL

https://app.rakuten.co.jp/services/api/IchibaItem/Ranking/20120927
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
genreId<br>*Genre ID* | long | Optional | The ID for specifying the genres used in Rakuten Ichiba<br>If it is necessary to lookup genre names and genre relationships, please use the Rakuten Genre search API (GenreSearch).<br>(*1) If no value for genre ID, gender, or age group is specified, all ranking information will be shown.<br>(*2) For other input parameter settings, please check the section on this page labeled "Items to be aware of regarding input parameters."
age<br>*Age group based* | integer | Optional | (*1) If no value for genre ID, gender, or age group is specified, all ranking information will be shown.<br>(*2) Age grouping and gender specifications can be used simultenously.<br>(*3) For other input parameter settings, please check the section on this page labeled "Items to be aware of regarding input parameters."
sex<br>*Gender based* | integer | Optional | (*1) If no value for genre ID, gender, or age group is specified, all ranking information will be shown.<br>(*2) Age grouping and gender specifications can be used simultenously.<br>(*3) For other input parameter settings, please check the section on this page labeled "Items to be aware of regarding input parameters."
carrier<br>*Platform* | integer | Optional | Choose the target platform for type of information to return: PC, mobile, or smartphone
page<br>*Page number* | integer | Optional | An integer between 1 and 34<br>*It is possible to specify rankings below 30th place.
period<br>*Period for ranking* | string | Optional | realtime: retrieve data in real time
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/IchibaItem/Ranking/20120927?applicationId=REPLACE_WITH_YOUR_APP_ID
##### Response

```json
{
  "title": "【楽天市場】ランキング市場 【総合】",
  "lastBuildDate": "Sat, 12 Dec 2015 03:50:33 +0900",
  "Items": [
    {
      "Item": {
        "rank": 1,
        "carrier": 0,
        "itemName": "おせちランキング185週以上1位達成!【博多久松】和洋折衷本格料亭おせち『博多』おせち2016★おせち料理≪おせち全46品≫博多久松おせち料理予約 特大おせち【楽ギフ_のし】",
        "catchcopy": "★9年連続グルメ大賞受賞！★お節ランキング185週以上1位達成!人気おせちがたったの2分で完売!おせち送料無料通販",
        "itemCode": "hisamatsu:10000014",
        "itemPrice": "15800",
        "itemCaption": "body {background-color: #000;}#osechiWrap{width:1200px;text-align:center;margin:20px auto;}#osechiWrap p{margin:0;}.mt5{margin-top:5px !important;}.mt10{margin-top:10px !important;}.mt15{margin-top:15px !important;}.mt20{margin-top:20px !important;}.mt25{margin-top:25px !important;}.mt30{margin-top:30px !important;}.mt40{margin-top:40px !important;}.mt50{margin-top:50px !important;}.cart_btn{margin-top:30px !important;}.cart_btn:hover{opacity:0.7;}.whiteLink{color:#fff;}",
        "itemUrl": "http://item.rakuten.co.jp/hisamatsu/2009hakata/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/hisamatsu/cabinet/2016osechi/kanban/bnr_hakata.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/hisamatsu/cabinet/2016osechi/kanban/bnr_hakata.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 1,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "2015-08-20 00:00",
        "endTime": "2015-12-31 00:00",
        "reviewCount": 16098,
        "reviewAverage": "4.49",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "博多久松",
        "shopCode": "hisamatsu",
        "shopUrl": "http://www.rakuten.co.jp/hisamatsu/",
        "genreId": "410890"
      }
    },
    {
      "Item": {
        "rank": 2,
        "carrier": 0,
        "itemName": "※間もなく早割終了！お歳暮＆年末早得クーポン有！2015年間ランキング総合部門受賞！三木谷社長も絶賛【総合1位/かに部門6年連続1位の蟹】[元祖カット済み生ずわい蟹大盛り1.2kg(総重量1.4kg)/化粧箱入/送料無料](2-3人前)[かに/カニ/蟹/鍋/御歳暮/かに 通販/カニ 通販]",
        "catchcopy": "＼ポイント最大10倍！今なら早割価格！／【早割12月21日9：59まで5,979円、12月21日10：00から6,478円】【贈答化粧箱包装】[かにしゃぶ/カニしゃぶ/ポーション/むき身/かに鍋/ますよね]",
        "itemCode": "masuyone:10000016",
        "itemPrice": "5979",
        "itemCaption": "■ お届け日 この部分は iframe 対応のブラウザでご覧ください。 ■ あす楽対応 12：00までのご注文であす楽対応 ※商品入荷状況により、稀にあす楽対応外の場合がございます。予めご了承ください。 対応不可エリア：北海道・九州・沖縄県・一部離島含む ※対応不可エリアには2日以降でお届け致します。 ※12時以降であす楽ご注文の場合は翌日発送になります。 ※時間指定・のし設定・銀行振込みは使用不可となります。 → あす楽についての詳細はこちら【北海道・沖縄県への配送料改定につきまして】2014年5月1日より送料無料商品でございます場合も、北海道・沖縄県への配送時、別途700円の送料を頂戴しております。また、決済方法を全額ポイント決済でいただいております場合は、【銀行振込または、代引き引換】にて別途700円の送料を御請求させていただきますので、何卒ご了承くださいませ。※手数料はお客様ご負担となっております。ご確認の程いただけますようお願い申し上げます。 ■ 商品内容 原材料：ズワイガニズワイ蟹足(天然)：ビードロカット（生/冷凍）約11〜15本 ズワイ蟹爪：リングカット（生/冷凍）約4〜6個 ズワイ蟹爪下：リングカット（生/冷凍）約4〜6本 ズワイカニ肩：ハーフカット（生/冷凍）約8〜12個 ※ズワイ蟹の大きさにより数量は前後します。 ※加熱用 ⇒合計1.2kgセット（総重量1.4kg）（2-3人前） 産地：ロシア/アメリカ(アラスカ)/ノルウェー産 ※冷凍時の重さです。解凍後は若干目減りあり。 ※品質保持のため、安全性の高い酸化防止剤（亜硫酸塩、エリソルビン酸Na）を使用しております。【お歳暮/御歳暮/おとりよせ/お取り寄せ/鍋】 販売者：有限会社増米商店（福井県敦賀市津内27-3-5） ■ 賞味期限 冷凍：1ヶ月(推奨1週間)以内　(冷凍-18℃以下で保存)※箱に印字の賞味期限は業務用の冷凍庫にて-18℃以下で保たれた一定の温度管理のもと保管をした場合の期限となっており、ご家庭用の冷凍庫の場合は、1ヶ月以内にお召し上がりくださいませ。（解凍後は当日中） 冷蔵：当日中 家庭用冷凍庫の場合、業務用冷凍庫に比べ保存温度が高いため品質が損なわれる可能性がございます。なるべく早めにお召し上がり下さいませ。 このページではインラインフレームを使用していますインラインフレームに未対応のブラウザをお使いの方は、こちらで内容をご確認いただけます。              この部分はインラインフレームを使用しています。 この部分はインラインフレームを使用しています。 この部分はインラインフレームを使用しています",
        "itemUrl": "http://item.rakuten.co.jp/masuyone/130007/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/masuyone/cabinet/goods/hp/hp2015_hyo_20151124.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/masuyone/cabinet/goods/hp/hp_salesa_talkb_201.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/masuyone/cabinet/common/topics/nenmatu_400_20151125.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/masuyone/cabinet/goods/hp/hp2015_hyo_20151124.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/masuyone/cabinet/goods/hp/hp_salesa_talkb_201.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/masuyone/cabinet/common/topics/nenmatu_400_20151125.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 1,
        "asurakuClosingTime": "12:00",
        "asurakuArea": "群馬県/埼玉県/千葉県/東京都/神奈川県/新潟県/富山県/石川県/福井県/山梨県/青森県/長野県/岐阜県/静岡県/愛知県/三重県/滋賀県/京都府/大阪府/兵庫県/奈良県/岩手県/和歌山県/鳥取県/島根県/岡山県/広島県/山口県/徳島県/香川県/愛媛県/高知県/宮城県/秋田県/山形県/福島県/茨城県/栃木県",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 33600,
        "reviewAverage": "4.41",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "越前かに問屋「ますよね」",
        "shopCode": "masuyone",
        "shopUrl": "http://www.rakuten.co.jp/masuyone/",
        "genreId": "304570"
      }
    },
    {
      "Item": {
        "rank": 3,
        "carrier": 0,
        "itemName": "【セット組】関ジャニ∞リサイタル　お前のハートをつかんだる!!【Blu-ray初回プレス仕様】＆【DVD初回プレス仕様】 [ 関ジャニ∞ ]",
        "catchcopy": "【楽天ブックスならいつでも送料無料】",
        "itemCode": "book:17724510",
        "itemPrice": "11500",
        "itemCaption": "関ジャニ∞【vg8】 発売日：2016年01月27日 予約締切日：2016年01月23日 株式会社ジェイ・ストーム／インフィニティ・レコーズ 初回限定 JAN：2100010401403 DVD ブルーレイ ミュージック・ライブ映像",
        "itemUrl": "http://item.rakuten.co.jp/book/13521034/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1403/2100010401403.gif?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1403/2100010401403.gif?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "楽天ブックス",
        "shopCode": "book",
        "shopUrl": "http://www.rakuten.co.jp/book/",
        "genreId": "505042"
      }
    },
    {
      "Item": {
        "rank": 4,
        "carrier": 0,
        "itemName": "ボタニカル　シャンプー★今だけ！最大1,500円OFF★BOTANIST　ボタニスト　ボタニカル シャンプー490ml／ボタニカル トリートメント490gボタニカル シャンプー トリートメント ボタニスト BOTANISTオーガニック ヘアケア コンディショナー ノンシリコン シャンプー",
        "catchcopy": "≪天然植物成分90％以上で優しいボタニカルシャンプー&トリートメント≫",
        "itemCode": "kobe-beauty-labo:10000193",
        "itemPrice": "1512",
        "itemCaption": "同一注文の別々での出荷がシステム上できかねますので、すべて同梱にて入荷後出荷させていただきます。あらかじめご了承くださいませ。 ※出荷状況：12月中旬より順次発送いたします。⇒当店からのメールが届かないお客様へ数々のランキングを受賞致しました。◆楽天市場 総合 ランキング1位獲得(2015/2/24付)◆美容・コスメ・香水 ランキング1位獲得(2015/2/24付)◆ヘアケア ランキング1位獲得(2015/2/24付)◆ヘアシャンプー ランキング1位獲得(2015/2/24付)◆アメリカ TOP RANKED SHAMPOOS\"NO1\"(2015/2/9付)◆フランス Mode＆beaute\"NO1\"(2015/1/29付) ※ボタニスト詰め替え用の販売は当サイトでは行っておりません 商品名 BOTANIST ボタニカル シャンプー 商品区分 化粧品 容量 各490ml 成分【モイスト】 水、グリセリン、コカミドプロピルベタイン、ココイルメチルタウリンNa、ラウロイルメチルアラニンNa、ラウラミドプロピルベタイン、ラウロイルサルコシンNa、ラウレス-4カルボン酸Na、ココイルグルタミン酸Na、デシルグルコシド、グリチルリチン酸2K、サトウキビエキス、セラミド2、PEG-30フィトステロール、加水分解ヒアルロン酸、加水分解コラーゲン、コカミドMEA、リンゴ酸、ポリクオタニウム-10、エタノール、BG、DPG、セテアレス-60ミリスチルグリコール、PPG-4セテス-20、EDTA-2Na、メチルイソチアゾリノン、メチルクロロイソチアゾリノン、香料 【スムース】 水、ヒドロキシアルキル（C12-14）ヒドロキシエチルサルコシン、ココイルメチルタウリンNa、ラウロイルサルコシンNa、コカミドプロピルベタイン、ラウレス-4カルボン酸Na、セラミド2、加水分解ヒアルロン酸、PEG-30フィトステロール、サトウキビエキス、グリチルリチン酸2K、加水分解ケラチン（羊毛）、デシルグルコシド、コカミドMEA、ジステアリン酸PEG-150、リンゴ酸、PEG-400、ポリクオタニウム-10、BG、DPG、PPG-4セテス-20、EDTA-2Na、塩化Na、エタノール、メチルイソチアゾリノン、メチルクロロイソチアゾリノン、香料 生産日本商品説明【モイスト】 ・天然植物由来成分90％以上配合(※90％以上をを植物由来成分と水で構成)・華やかさを彩るアプリコットとジャスミンのダブルフレグランス・お子様とご一緒にお使え頂けます。弱酸性の「せっけん成分」で地肌から潤い仕上がりに【スムース】・天然由来植物成分90％配合(※90％以上をを植物由来成分と水で構成)・華やかさを彩るグリーンアップルとローズのダブルフレグランス・子どもも使える安心設計。「せっけん成分」で刺激物から身を守り、水分を保ちます。※商品によってお届けの際に、外側のフィルムがついているものとついていないものがありますが、商品の仕様に違いはありませんのでご安心ください。 メーカー名(株)I-ne 06-6245-2339 広告文責株式会社メインライン　0120-777-034 商品名 BOTANIST ボタニカル トリートメント 商品区分 化粧品 容量 各490g 成分【モイスト】 水、 ジメチコン、 セテアリルアルコール、 グリセリン、 ベヘントリモニウムクロリド、 マカデミアナッツ油、 オレイン酸オレイル、 ビスセテアリルアモジメチコン、 セラミド2、 PEG-30フィトステロール、 ヒアルロン酸Na、 アルキル（C12,14）オキシヒドロキシプロピルアルギニンHCl、 加水分解ヒアルロン酸、 加水分解コラーゲン、 ジラウロイルグルタミン酸リシンNa、 リンゴ酸、 セタノール、 BG、 DPG、 PPG-4セテス-20、 イソアルキル（C-10-40)アミドプロピルエチルジモニウムエトサルフェート、 ステアルトリモニウムクロリド、 ベヘントリモニウムメトサルフェート、 エタノール、 イソプロパノール、 アミノプロピルジメチコン、 メチルイソチアゾリノン、 メチルクロロイソチアゾリノン、 香料【スムース】水、セタノール 、ジメチコン、グリセリン、DPG、ベヘントリモニウムクロリド、アボカド油、セラミド2、加水分解ヒアルロン酸、PEG-30フィトステロール、イソアルキル（C10-40）アミドプロピルエチルジモニウムエトサルフェート、加水分解ケラチン（羊毛）、ヒアルロン酸Na、ジリノール酸ジイソプロピル、イソステアリン酸イソステアリル、リンゴ酸、乳酸、BG、ステアルトリモニウムクロリド、ベヘントリモニウムメトサルフェート、PPG-4セテス-20、イソプロパノール、シクロペンタシロキサン、（ビスイソブチルPEG-14／アモジメチコン）コポリマー、アモジメチコン、メチルイソチアゾリノン、メチルクロロイソチアゾリノン、香料 生産日本商品説明【モイスト】 ・天然植物由来成分90％以上配合(※90％以上をを植物由来成分と水で構成)・上品さを彩るアップル＆ベリーのダブルフレグランス・毛先のケアに注目した成分で毛先までしっとり潤い指どおり艶やかな髪へと保ちます。【スムース】・天然由来植物成分90％配合(※90％以上をを植物由来成分と水で構成)・上品さを彩るアップル＆ベリーのダブルフレグランス・肌や頭皮のバリア機能を整え、うるおいを閉じこめます。また、髪の弾力とツヤに必要な水分を抱える力を高めます。※商品によってお届けの際に、外側のフィルムがついているものとついていないものがありますが、商品の仕様に違いはありませんのでご安心ください。 メーカー名(株)I-ne 0120-333-476 広告文責株式会社メインライン　0120-777-034.botacouponA{width:1100px;height:1900px;margin:60px auto 0;background-color:#f1eee0;text-align:center;} ※詰め替え（シャンプー＆トリートメント）の種類はお選びいただけません。予めご了承ください。 ※注文後のクーポン適応および変更はお受けできかねますのでご注意ください。 ※トートバックには数に限りがございますので、無くなり次第終了とさせていただきます ⇒クーポンのご利用に関してはこちらをご参照ください。 この部分は iframe 対応のブラウザで見てください。 【BOTANIST】 シャンプー&トリートメント 【BOTANIST】 ヘアオイル 【SALONIA】 モイストイオンドライヤー 【SALONIA】 アボカドヘアオイル 【SALONIA】 カールアイロン32mm 【SALONIA】 ストレートヘアアイロン 【SALONIA】 ロールブラシ26mm 【SALONIA】 2WAY ストレート&カール",
        "itemUrl": "http://item.rakuten.co.jp/kobe-beauty-labo/bota-01/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kobe-beauty-labo/cabinet/04278206/imgrc0065298642.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kobe-beauty-labo/cabinet/04278206/04288900/bota_sam.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kobe-beauty-labo/cabinet/04278206/imgrc0065208306.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kobe-beauty-labo/cabinet/04278206/imgrc0065298642.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kobe-beauty-labo/cabinet/04278206/04288900/bota_sam.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kobe-beauty-labo/cabinet/04278206/imgrc0065208306.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 1,
        "shipOverseasArea": "ワールドワイド",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 18354,
        "reviewAverage": "4.28",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "SALONIAオフィシャルサイト",
        "shopCode": "kobe-beauty-labo",
        "shopUrl": "http://www.rakuten.co.jp/kobe-beauty-labo/",
        "genreId": "210677"
      }
    },
    {
      "Item": {
        "rank": 5,
        "carrier": 0,
        "itemName": "【速報！2015楽天年間ランキング食品部門第1位獲得！】年末年始配送日指定OK！特大タラバ蟹！船上ボイル→船上凍結厳選！特大/極太/タラバ蟹/たらば蟹ボイルタラバ蟹/かに/カニ/蟹/たらば/タラバ/1kg/2kg/3kg/5kg",
        "catchcopy": "食べごたえ抜群！タラバ蟹の2015楽天年間1位のタラバ蟹！漁獲後すぐに船上で塩水ボイルして急速凍結！特大サイズで身入り抜群のタラバ蟹！",
        "itemCode": "sfd-ymt:10000345",
        "itemPrice": "6480",
        "itemCaption": "●商　品特大！極上！ボイルタラバ蟹脚 カニ / かに / たらば / 目 安：※肩数は個体差で前後します1kg＝1〜2肩前後 冷凍時の状態で1kgですので解凍時は若干目減りする場合があります。 原材料：本タラバ蟹、塩 保存方法：−18℃以下で保存 賞味期限：冷凍1ヶ月　冷蔵2日 原産国：ロシア産一部脚折れが混じる場合もございますが味、品質は1級品です！●脚折れが混じる場合もございます味、品質には全く問題ございません。●送　料送料無料 ※送料無料商品と同梱で送料無料！ ※代引手数料315円はお客様御負担 ※沖縄県配送追加1，000円　 その他離島配送追加500円●配送方法クロネコヤマト （クール冷凍配送)配送日時指定がある場合は、注文の際にお申し付け下さい。 天候、在庫の都合で指定日の到着がずれることもございます。 わけまち・訳まち・ワケマチ・わけ待ち ●同梱について 冷凍商品と同梱可能 輸入者：株式会社YAMATO 住所：宮城県塩釜市新浜町3-13-14 ◆今年は例年よりも原料段階での脚折れ が多い状況です。ロットにより脚折れが 多く入る場合がございますが、 味・品質には問題ございません。●お値打ち価格！当店オススメ商品はこちら●",
        "itemUrl": "http://item.rakuten.co.jp/sfd-ymt/869808/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sfd-ymt/cabinet/00661828/imgrc0064116443.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sfd-ymt/cabinet/00661828/img57219721.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sfd-ymt/cabinet/00661828/imgrc0064116443.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sfd-ymt/cabinet/00661828/img57219721.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 1,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 17069,
        "reviewAverage": "4.2",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "海の幸なのにYAMATO",
        "shopCode": "sfd-ymt",
        "shopUrl": "http://www.rakuten.co.jp/sfd-ymt/",
        "genreId": "410776"
      }
    },
    {
      "Item": {
        "rank": 6,
        "carrier": 0,
        "itemName": "関ジャニ∞リサイタル　お前のハートをつかんだる!!【DVD初回プレス仕様】 [ 関ジャニ∞ ]",
        "catchcopy": "【楽天ブックスならいつでも送料無料】",
        "itemCode": "book:17724503",
        "itemPrice": "5500",
        "itemCaption": "関ジャニ∞【vg8】 発売日：2016年01月27日 予約締切日：2016年01月23日 株式会社ジェイ・ストーム／インフィニティ・レコーズ 初回限定 JABAー5231/5232 JAN：2100010401205 DVD ミュージック・ライブ映像 邦楽 ロック・ポップス",
        "itemUrl": "http://item.rakuten.co.jp/book/13521015/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1205/2100010401205.gif?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/1205/2100010401205.gif?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "楽天ブックス",
        "shopCode": "book",
        "shopUrl": "http://www.rakuten.co.jp/book/",
        "genreId": "300339"
      }
    },
    {
      "Item": {
        "rank": 7,
        "carrier": 0,
        "itemName": "【ポイント最大19倍】カニしゃぶ 福袋 約1.8kg楽天リアルタイムランキング総合1位獲得生冷凍 ズワイガニのカニ爪、むき爪下、肩肉の当店一番人気カニセットかにしゃぶ、カニ鍋など色々なカニ料理に大活躍！ギフト お歳暮",
        "catchcopy": "楽天リアルタイムカニランキング1位獲得のカニセット 生冷凍 ズワイガニのカニ爪、むき爪下、肩肉の当店一番人気カニセット かにしゃぶ、カニ鍋など色々なカニ料理に大活躍！",
        "itemCode": "kanikoubou:10001578",
        "itemPrice": "4680",
        "itemCaption": "■商品内容■カニしゃぶ カニ鍋に最適1品目【生冷凍】ズワイガニむき爪下約400g2品目【生冷凍】ズワイガニむき爪約400g 3品目【生冷凍】ズワイガニ肩肉ハーフカット約1kg(個数の目安：15〜30個前後)※すべて冷凍状態での重さです。※すべて加熱調理用です。必ず加熱してからお召し上がり下さい。 ■お召し上がり人数■およそ3人前※お野菜など入れる具材の量などで前後いたします。■原材料■本ズワイガニ(ロシア・アラスカ・カナダ産)、酸化防止剤（エリソルビン酸Na、チャ抽出物、亜硫酸塩）加工地：北海道■お召し上がり方■1.必要な分だけ箱から取り出し、他の袋に入れ、袋の上から流水をあてて解凍します。芯が多少、凍っている程度で解凍はOKです。2.カニしゃぶ、カニ鍋、天婦羅、バター焼きなど、必ず加熱調理して色々なお料理でお召し上がりください。※中骨がありますので、誤って飲み込まないようにご注意ください。※室温や冷凍庫内で自然解凍するとカニの旨味が抜けたり、黒く変色することがあります。詳しい調理方法は添付されるお召し上がり方法をご参照ください。■賞味期限■賞味期限は袋または箱側面に記載しております。冷凍（-18℃以下）保存で約30日。解凍後はすぐにお召し上がりください。※生鮮品の為、お早目にお召し上がりください。■製造者■有限会社マルイ水産北海道網走市大曲1丁目14番地19号■お届け日■ご注文後3〜5日以内に出荷いたします。着日指定の際は、ご注文日より6日後〜30日以内でご指定ください。※お急ぎの方は当店までご連絡ください。■送料＆配送方法■北海道 980円、本州四国九州 1,620円一部地域をのぞき全国送料無料！※沖縄県は別途送料が2,120円必要です。返品については、こちらをご確認ください >>>お歳暮ギフトや贈答用にも最適な1.8kg詰めカニセット！超人気カニしゃぶカニ鍋セット★累計50,000セット以上を販売してきてレビューも3,700件以上ついた実力!!殻むき済みの蟹爪とむき爪下、肩肉の詰め合わせです。特にカニ爪はプリプリ、シコシコとした歯ごたえが特徴で、蟹しゃぶはもちろん、蟹鍋、かにフライ、かにの天ぷらなど楽しみ方がいろいろ♪福袋のため、かに爪、爪下のサイズが異なることをご了承ください。1.8kg詰めで3人での蟹シャブや蟹なべに最適です。一部地域を除いて送料無料でお届けします！(※沖縄県は別途送料2,120円かかります)■この商品の関連キーワード■ かにしゃぶ,かに鍋,カニ料理,カニフライ,カニ爪,カニ 天ぷら,カニ 鍋,ズワイガニ,ずわいがに,カニ,かに,蟹,蟹シャブ,蟹しゃぶ,かにつめ,蟹爪,蟹つめ,蟹なべ,蟹鍋,カニ鍋,ズアイガニ,ずあいがに,カニ ランキング,お歳暮,御歳暮インラインフレームインラインフレームインラインフレームズワイガニ かにしゃぶ福袋1.8kgかにしゃぶ福袋セット内容かにしゃぶ福袋 調理例かにしゃぶ福袋のレビュー インラインフレームインラインフレームインラインフレームインラインフレームインラインフレームインラインフレームインラインフレームインラインフレーム",
        "itemUrl": "http://item.rakuten.co.jp/kanikoubou/1424039/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kanikoubou/cabinet/s_photo/img62608828.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kanikoubou/cabinet/s_photo/img60990654.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kanikoubou/cabinet/s_photo/img62608828.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/kanikoubou/cabinet/s_photo/img60990654.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 3743,
        "reviewAverage": "3.99",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "海鮮蟹工房",
        "shopCode": "kanikoubou",
        "shopUrl": "http://www.rakuten.co.jp/kanikoubou/",
        "genreId": "509647"
      }
    },
    {
      "Item": {
        "rank": 8,
        "carrier": 0,
        "itemName": "【3DS】モンスターハンタークロス【12月20日頃 出荷予定】 【税込】 カプコン [CTR-P-BXXJ]【返品種別B】【送料無料】【RCP】",
        "catchcopy": "【Joshinは平成20/22/24年度製品安全対策優良企業 連続受賞・Pマーク取得企業】",
        "itemCode": "jism:11179595",
        "itemPrice": "5190",
        "itemCaption": "在庫状況：入荷次第出荷出荷予定：12月20日□「返品種別」について詳しくはこちら□■新製品■2015年11月 発売＜出荷目安＞・12/8（火）9:59までにご注文分出荷日→12/13（日）予定・12/8（火）10:00以降のご注文分出荷日→12/20（日）予定※ご注文に関しましては、お1人様1点でお願いします。複数ご購入はご遠慮ください。複数ご購入された場合はご注文のお取り消しをさせて頂く場合がございます、予めご了承下さい。※3D映像の見えかたには個人差があります。体調や体質、映像の内容、周囲の状況などによって3D映像に見えない場合もありますので、あらかじめご了承ください。※6歳以下のお子様は、長時間3D映像を見続けると目の成長に悪い影響を与える可能性がありますので、2D表示でご使用ください。※数量限定特典：ニンテンドー3DS『モンスターハンタークロス』オリジナルテーマ（2種）ダウンロード番号（封入）付きは終了しました。◇◆商品紹介◇◆クロスし、個性を生み出すハンティングアクション『モンスターハンタークロス』が登場！　！　◆全てのジャンルの新たな可能性を引き出す　武器全14種。大剣、太刀、片手剣、双剣、ハンマー、狩猟笛、ランス、ガンランス、スラッシュアックス、チャージアックス、操虫棍、ライトボウガン、ヘビィボウガン、弓“狩技”、“狩猟スタイル”とクロスさせる（掛け合わせる）ことで、“自分だけのハンティング”を生み出そう！　◆ハンターの可能性を広げる“狩技”一撃で大ダメージをモンスターに与える技、自らに驚異的な力を与える技、周囲を癒す技など、様々な“狩技”が存在する。◆4種の個性的なハンティングが選べる“狩猟スタイル”“狩猟スタイル”を選択することで空間を制する者、ピンチをチャンスに変える者…様々な個性が生み出される！　◆4大メインモンスター現る！　！　本作では4頭のメインモンスターが登場する。それぞれ異なる特徴や生態を持ち、すべてのハンターは未体験のハンティングに遭遇する！　◆懐かしさと新しさがクロスするシリーズ初登場の「ベルナ村」からファンの方はニヤリとする懐かしの村（「ココット村」「ポッケ村」「ユクモ村」）まで、様々な要素がクロスされて登場する。◆製品詳細◆対応機種　：　ニンテンドー3DS/ニンテンドー3DS LL/Newニンテンドー3DS/Newニンテンドー3DS LLジャンル　：　ハンティングアクションプレイ人数　：　1人（通信プレイ時：最大4人）CERO審査　：　15歳以上（C）CAPCOM CO. LTD. 2015 ALL RIGHTS RESERVED.(※この説明文は楽天市場店の記載内容です。URLはhttp://item.rakuten.co.jp/jism/で始まります。URLが異なる際はサイトを利用することのないよう十分ご注意ください。)おもちゃ＞TVゲーム＞ニンテンドー3DS＞3DS専用ソフト＞アクション・格闘・シューティング▲この商品の該当カテゴリページへは、こちらから参照できます。・ご購入はお1人様1本でお願いします。同一商品を複数ご購入された場合は、ご注文を承りましたという自動メール送信後でありましても、全てのお買い物を取り消し（キャンセル）をさせていただく場合があります。またお名前が異なってもお届け先が同じ場所の場合は、複数購入と判断する場合がございますのでご了承願います。・商品の返品・交換についてTVゲーム関連商品の返品・交換はお受けできません。但し、初期不良の場合、1週間以内にJoshin web事務局までご連絡ください。 ※ お客様の都合による返品・交換もお受けできませんので、ご了承ください。個人情報を記録するハードディスク内蔵モデルは、初期不良でありましてもJoshin webで良品への交換は出来ません。初期不良の場合はメーカーの連絡先をご案内いたしますので、お客様から直接メーカーへ連絡していただくようお願いいたします。※液晶モニターについてゲームに使用されている液晶モニターは、精密度の高い技術で生産されていますが、黒い点が現れたり、赤・青・緑の点が消えないことがあります。(ドット抜け)これらの症状は製品の仕様的な物で故障ではございません。交換などもできませんのであらかじめ、ご了承ください。・ゲーム機本体の修理ゲーム機本体の修理はメーカー直接対応となります。説明書に記載されているメーカーサポートにご連絡ください。・在庫のない商品の納期について在庫がない商品（「入荷次第出荷」と表示）は1週間程度商品入荷までお待ちいただく場合があります。・予約商品について但し、発売日4日前までのご注文の場合。（一部地域を除く）新作（未発売商品）につきましては、発売日の4日以上前にご予約をいただきました場合は、原則として発売日当日のお届けになります。（一部商品を除く）　詳しくはこちらお客様より、発売日前のお届け希望日の指定をいただきましても、お届けは発売日となります。お届け予定日の変更連絡は致しておりません、また大阪市内より発売日の前日に出荷いたしますので、遠隔地（北海道、青森県、秋田県、沖縄県、一部郡部、離島地域）の場合は、発売日の翌日以降のお届けとなります。ご予約商品と家電製品などを一緒にご注文いただいた場合は、商品の発送が多少遅くなり発売日以降のお届けになります。ご予約商品を複数ご購入いただいた場合、または在庫商品とご予約商品を同時にご購入いただいた場合、あるいはお取り寄せ商品とご予約商品を同時にご購入いただいた場合は、すべての商品がそろってからの発送になりますのでご注意ください。(分割でのご発送はお受けできません）・メーカー予約特典についてメーカーが用意している予約特典が付いている場合は、商品名に以下の記載をしております。【特典付】→メーカーが用意している、特典が付きます。　　※表記の無い商品につきましては、特典が付きません。【抽選特典付】→メーカーが用意している特典の数量に限りがございます。当選者様のみ、商品と同梱しての発送になります。　　※抽選に外れた方への通知はいたしておりません。悪天候や災害の影響などにより、商品のお届けが遅れる場合がございます。またメーカーの都合により、商品のお届けが遅れる場合もございますので、ご了承願います。・商品の配送についてご予約商品を複数ご購入いただいた場合、または在庫商品とご予約商品を同時にご購入いただいた場合、あるいはお取り寄せ商品とご予約商品を同時にご購入いただいた場合は、すべての商品がそろってからの発送になります。お急ぎの場合は、お手数ですがご注文を分けていただきますようお願いいたします。Joshin web オススメゲーム(※この説明文は楽天市場店の記載内容です。URLはhttp://item.rakuten.co.jp/jism/で始まります。URLが異なる際はサイトを利用することのないよう十分ご注意ください。)",
        "itemUrl": "http://item.rakuten.co.jp/jism/4976219068239-54-18116-n/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/jism/cabinet/0434/4976219068239.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/jism/cabinet/0434/4976219068239.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 1,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 617,
        "reviewAverage": "4.57",
        "pointRate": 2,
        "pointRateStartTime": "2015-11-29 16:00",
        "pointRateEndTime": "2016-01-28 09:59",
        "shopName": "Joshin web 家電とPCの大型専門店",
        "shopCode": "jism",
        "shopUrl": "http://www.rakuten.co.jp/jism/",
        "genreId": "562885"
      }
    },
    {
      "Item": {
        "rank": 9,
        "carrier": 0,
        "itemName": "期間限定1980円/2個購入でマンゴー味+最大1個/3個購入でさらにチアシード+最大1個プレゼント送料無料/グリーンスムージー/ダイエット/酵素/スムージー＜ミネラル酵素グリーンスムージー 選べる5種類＞Natural Healthy Standard",
        "catchcopy": "楽天で世界4冠＆国内楽天総合1位8回酵素×ミネラルでミキサー不要の超簡単ダイエットナチュラルヘルシースタンダードシェイカー付スムージー",
        "itemCode": "tenderly:10000017",
        "itemPrice": "1980",
        "itemCaption": "⇒よくお問い合わせいただく商品内成分についてお知らせです。 ※2〜5営業日以内に順次発送＜プレゼント対象条件＞期間：12/4（金）16：00〜12/14（月）11：59までに購入の方に限り※プレゼントはお一人様最大1個限りと致します。※2個以上購入の方に限りご使用可能◆ありがとうございます！おかげさまでスムージー100万個突破！ ◆楽天総合1位8回受賞＆世界4カ国の楽天でも1位受賞！ ◆世界中で大人気♪有名人・モデル愛飲中！ ◆送料無料＆専用シェイカープレゼント中♪ ◆スプーン付(スプーンは商品袋の中に入っています) ◆新発想のグリーンスムージー×ミネラル×酵素 ◆約200種類の野菜と果物エキスを贅沢mix！ ◆ミキサー要らずで10秒シェイク！作り方簡単♪◆ラ・フランス味復活で選べる6種類のフレーバー『ミネラル酵素グリーンスムージー』のよくあるご質問 ご購入前にご確認してみてください。 Q.1袋の内容量・カロリー・何ヶ月ですか？ A.1日6gを目安に約1か月分となっております。 カロリーの方は6gあたり、22〜24キロカロリーでございます。 使用上の注意をよく読みお飲みになってください Q.授乳・妊娠中・乳幼児の方の本商品の摂取について A.妊娠、授乳中の方も飲んで頂いても問題はありませんが、妊娠、授乳中はデリケートな時期ですので、こちらの商品を飲む場合は食物繊維などのお腹がゆるくなりやすい成分と、食事での栄養バランスに気をつけてほしいという意味で摂取をお控え下さいませ。こちらに入っております成分は飲んでも問題はございませんので、ご安心ください。 Q.飲むタイミング・飲み方・作り置きについて A.商品の飲むタイミングについては食事前がいいのではないかと思います。グルコマンナン、サイリウム、食物繊維などが入っていますので、効果的なのは3食のうち、一番量をとる食事の前に飲んで、食事の量を減らすのがいいかと思われます。1食置き換えるか、空腹前に飲んで食事量を減らすかではないかと思います。3食すべて置き換えなどの無理だけはお控えください。 Q.飲み方にについて A.常温以下でお飲みいただくをお薦めしております。 Q.作り置きにについて A.こちら商品はお召し上がる前にお作り下さいませ。 長時間放置しておりますと、グルコマンナンというこんにゃくの主成分である食物繊維が 固まってしまうため、作り置きでのお召し上がりはお辞め下さいませ。 商品名 ミネラル酵素グリーンスムージー　マンゴー味ミネラル酵素グリーンスムージー 豆乳抹茶味ミネラル酵素グリーンスムージー はちみつレモン味ミネラル酵素グリーンスムージー ピーチ味ミネラル酵素グリーンスムージー アセロラ味 商品区分 食品・アサイー末含有食品 内容量 いずれも200g 原材料 ※各商品リンクよりご確認下さい ミネラル酵素グリーンスムージー　マンゴー味 ミネラル酵素グリーンスムージー 豆乳抹茶味 ミネラル酵素グリーンスムージー はちみつレモン味 ミネラル酵素グリーンスムージー ピーチ味 ミネラル酵素グリーンスムージー アセロラ味ミネラル酵素グリーンスムージー ラ・フランス風味 使用法 いずれも栄養補助食品として1日約6g（付属スプーン約2杯分）を目安に、シェイカーに入れて約200cc位まで水または牛乳などを入れてよく混ぜてお召し上がりください。 保存方法 いずれも高温多湿、直射日光を避け涼しい所に保管してください。 栄養成分表示6gあたり ※各商品リンクよりご確認下さい ミネラル酵素グリーンスムージー　マンゴー味 ミネラル酵素グリーンスムージー 豆乳抹茶味 ミネラル酵素グリーンスムージー はちみつレモン味 ミネラル酵素アサイースムージー ピーチ味 ミネラル酵素グリーンスムージー アセロラ味 ミネラル酵素グリーンスムージー ラ・フランス風味 ご使用上の注意 いずれも開封後はお早めにお召し上がりください。体質に合わない方は、使用を中止してください。薬を服用している方、通院中の方は担当の専門医にご相談の上ご使用ください。食品アレルギーのある方は原材料表示をご参照ください。妊娠・授乳中の方は身体的にデリケートな時期ということを考慮し、念のためご使用はお控えください。 生産日本 賞味期限 いずれも商品裏面に記載 製造・販売業者 いずれも(株)テンダリー 〒550-0013 大阪市西区新町1-6-18-3F 広告文責いずれも(株)テンダリー06-6541-2577 html,body {margin:0;padding:0;position:relative;}.saloframe {line-height:1;text-align:center;color:#000;}.saloframe img {vertical-align:bottom}＜プレゼント対象条件＞期間：12/4（金）16：00〜12/14（月）11：59までに購入の方に限り ※プレゼントはお一人様最大1個限りと致します。※2個以上/3個以上購入の方に限りご使用可能※条件：併用不可/お一人様1回限り※店内商品購入に限りご使用可能※使用期間：12/4（金）16：00〜12/14（月）11：59 このページではインラインフレームを使用しています ※条件：併用不可/お一人様1回限り ※店内商品購入に限りご使用可能 ※使用期間：12/4（金）16：00〜12/14（月）11：59 ＜プレゼント対象条件＞ 期間：12/4（金）16：00〜12/14（月）11：59までに購入の方に限り ※プレゼントはお一人様最大1個限りと致します。※2個以上/3個以上購入の方に限りご使用可能",
        "itemUrl": "http://item.rakuten.co.jp/tenderly/ten-green-01/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/tenderly/cabinet/04436979/imgrc0068510691.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/tenderly/cabinet/04576669/imgrc0069211747.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/tenderly/cabinet/04576669/imgrc0069211748.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/tenderly/cabinet/04436979/imgrc0068510691.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/tenderly/cabinet/04576669/imgrc0069211747.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/tenderly/cabinet/04576669/imgrc0069211748.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 1,
        "shipOverseasArea": "ワールドワイド",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 20230,
        "reviewAverage": "4.24",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "Natural Healthy Standard",
        "shopCode": "tenderly",
        "shopUrl": "http://www.rakuten.co.jp/tenderly/",
        "genreId": "563732"
      }
    },
    {
      "Item": {
        "rank": 10,
        "carrier": 0,
        "itemName": "板前魂の花籠　和風三段重おせち料理　3人前　全33品目　おせち 2016 送料無料　お節料理　おせち",
        "catchcopy": "当店売上No1楽天総合ランキング1位おせち！（2011年12月4日付総合デイリーランキング）/累計57万セット完売/おせち　お取り寄せ/冷凍食品/おせち 3人/特選/ランキング/お節 /お正月/",
        "itemCode": "2-itamae:10000394",
        "itemPrice": "9980",
        "itemCaption": "#products_detail {width:450px;background:#ffffff;padding:12px 0pt 0pt 0pt;color:#000000;border:2px solid #CCCCCC}div#products_detail p {margin-bottom:8px}table.recipe,table.info{width:100%;}table.recipe {border: solid 1px #dcdcdc; border-collapse: collapse;}table.recipe th {border:1px solid #DCDCDC}table.recipe td {font-size:medium;padding:5px 0pt 0pt 12px;border:1px solid #DCDCDC;line-height:140%}table.info th {background-color:#000000;color:#FFFFFF}table.info td {padding:12px;}span.strong{color:#FF0000;font-weight:bold;}td a:link {color:#0000FF;}div#products_detail h2 {text-align:center;border-bottom:1px solid #CCCCCC;font-size:20px}当店人気No1　三段重　和風おせち料理　白木箱　　板前魂おせち2016よくお読みください【重要】ご注文後すぐに発送準備に入ります為、変更やキャンセルはお受けできません。　商品/配送先/配送日時指定にお間違いが無いか、ご確認頂いた上でご注文ください。当店のおせち料理は冷凍おせち料理となります。お支払い方法について銀行振り込み、郵便振替え、代金引換、楽天バンク決済、クレジットカード決済がご利用いただけます。11月17日以降はお振込みでのお支払いをお受けしておりません商品内容全33品目 3人前 お品書き、解凍・保存方法案内付き原産国・アレルゲン表記につきましてはこちらを御覧ください。名称おせち重箱サイズ 20.5×20.5×4.5cm/材質:白木消費期限冷凍の状態で2016年1月15日迄。解凍後冷蔵庫保管で2日間保存方法要冷凍（-18℃以下）解凍方法自然解凍してください。冷蔵庫で約24時間〜36時間 ※あくまで目安とお考え下さい配送について送料は無料ですクール冷凍便　での配送になります。※伊豆諸島内の青ヶ島村、神津島村、利島村、新島村、御蔵島村、三宅村および小笠原諸島の小笠原村へのお届けは冷凍クール便のサービスエリア外になるためお届けできません。同梱についておせち料理の同梱発送はできません。個別配送となります。熨斗について対応しておりません領収書についてご希望の方はご注文時に「領収書希望」と備考欄にご記入ください 。領収書の発行は年明けになります。ご了承下さい。製造者〒533-0013　大阪府大阪市東淀川区豊里1−3−23有限会社ナカノモードエンタープライズ会社概要会社概要#pagebody .rakutenLimitedId_ImageMain1-3 { margin: 0px 0px 0px 10em;}",
        "itemUrl": "http://item.rakuten.co.jp/2-itamae/sandannp/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/2-itamae/cabinet/2016/thumb/hanakago_kago_01.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/2-itamae/cabinet/2016/thumb/hanakago_kago_01.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "2015-08-23 10:00",
        "endTime": "2015-12-31 23:59",
        "reviewCount": 10375,
        "reviewAverage": "4.23",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "板前魂 おせち",
        "shopCode": "2-itamae",
        "shopUrl": "http://www.rakuten.co.jp/2-itamae/",
        "genreId": "410890"
      }
    },
    {
      "Item": {
        "rank": 11,
        "carrier": 0,
        "itemName": "三代目 J Soul Brothers LIVE TOUR 2015 「BLUE PLANET」 【DVD3枚組+スマプラ】 【初回生産限定】 [ 三代目 J Soul Brothers from EXILE TRIBE ]",
        "catchcopy": "【楽天ブックスならいつでも送料無料】",
        "itemCode": "book:17652772",
        "itemPrice": "4972",
        "itemCaption": "三代目 J Soul Brothers from EXILE TRIBE 三代目 J Soul Brothers from EXILE TRIBEBKSCPN_【ss_sale12】 発売日：2015年12月16日 予約締切日：2015年12月12日 エイベックス・ミュージック・クリエイティヴ(株) 初回限定 RZBDー86013/5 JAN：4988064860135 SANDAIME J SOUL BROTHERS LIVE TOUR 2015 [BLUE PLANET] DVD ミュージック・ライブ映像 邦楽 ロック・ポップス",
        "itemUrl": "http://item.rakuten.co.jp/book/13436671/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0135/4988064860135.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0135/4988064860135_2.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0135/4988064860135_3.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0135/4988064860135.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0135/4988064860135_2.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/0135/4988064860135_3.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 88,
        "reviewAverage": "4.91",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "楽天ブックス",
        "shopCode": "book",
        "shopUrl": "http://www.rakuten.co.jp/book/",
        "genreId": "300339"
      }
    },
    {
      "Item": {
        "rank": 12,
        "carrier": 0,
        "itemName": "【2014年SOYジャンル賞受賞店】【送料無料】メダリストワンデープラス 30枚パック 6箱セット （　メダリストワンデー　/　メダリスト ワンデープラス　/　メダリスト　/ メダリスト1day　）",
        "catchcopy": "※画像内の価格は税別です※※処方箋不要※",
        "itemCode": "sigma-contact:10000057",
        "itemPrice": "6396",
        "itemCaption": "【処方箋不要】※左右同じ度数の場合でも必ず左右ともPWR(度数)のご入力お願いします。※本製品数量1につき右3箱左3箱の割り振りです。＝ご注文前にご確認ください＝◆ジョンソン・エンド・ジョンソン社製品販売についての重要なお知らせ◆◆メーカー欠品（受注制限）情報◆◆使い捨てコンタクトレンズご購入に関する遵守事項について◆◆1注文あたりのご購入箱数の上限について◆◆返品・交換に関する大事なご案内◆商品スペック処方箋処方箋不要商品名メダリストワンデープラス 30枚パック 6箱セット商品解説「メダリスト ワンデー プラス」は、『レンズデザイン』 『レンズ保存液』 『レンズ素材』のレンズ構成要素を研究し、3つの要素が相乗効果を発揮する “コンフォート モイスト テクノロジー” を開発。瞬きのたびに涙がレンズ全体に広がり、本物のうるおい感を実現します。装用終日装用交換期限1日直径14.2mmベースカーブ8.6mmのみ。ご注文時に登録の必要はございません。枚数30枚×6箱=180枚　両眼3カ月分右3箱左3箱医療機器承認番号21700BZY00170000",
        "itemUrl": "http://item.rakuten.co.jp/sigma-contact/m1p-06/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sigma-contact/cabinet/1day/02371192/imgrc0063794319.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sigma-contact/cabinet/02987433/img57990365.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sigma-contact/cabinet/1day/02371192/imgrc0062116117.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sigma-contact/cabinet/1day/02371192/imgrc0063794319.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sigma-contact/cabinet/02987433/img57990365.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/sigma-contact/cabinet/1day/02371192/imgrc0062116117.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 1,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 60683,
        "reviewAverage": "4.73",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "シグマ　コンタクト",
        "shopCode": "sigma-contact",
        "shopUrl": "http://www.rakuten.co.jp/sigma-contact/",
        "genreId": "402804"
      }
    },
    {
      "Item": {
        "rank": 13,
        "carrier": 0,
        "itemName": "☆送料無料☆＆【お試し割引価格】（お一人様一回限り最大4ビンまで）UMF協会認定マヌカハニー UMF10+　250g100％純粋非加熱　はちみつ",
        "catchcopy": "レビュー5000件！マヌカハニーの味がダメだったお客様も絶賛☆",
        "itemCode": "honeymother:10000018",
        "itemPrice": "2900",
        "itemCaption": "ギフト対応　 100％天然純粋＆非加熱はちみつ商品名UMF協会認定　マヌカハニー 10+内容量250g賞味期限2年以上保存方法高温多湿・直射日光を避けて保存して下さい原材料100％天然純粋＆非加熱はちみつ原産国ニュージーランドハニーマザーのマヌカハニー にはキャラメルのようなコクと香ばしさがあり、後味のさわやかさに、本物の味を感じるハチミツです。※非加熱の生はちみつですので、一歳未満のお子様には与えないで下さい。（妊娠中や授乳期の方はお召し上がりいただけます）店長の西田恵美子です。 夫のニュージーランド赴任をきっかけにマヌカハニーと出会いました。 夫が帰国後、マヌカハニーを探しましたが当時は日本にまだなく、「それでは私が！」 と思い、消費生活アドバイザーという資格を活かし、マヌカハニーの輸入を始めました。 気づけばマヌカハニーを扱って18年目。 たくさんのお客様に支えられながら 「本物のマヌカハニーをより多くの方に召しあがっていただきたい！」 その思いでこれからも本物の商品をお届けします。ハニーマザースタッフ紹介 UMF協会認定お試し マヌカハニー10＋　送料無料　証明書付き同梱商品がある場合でも送料無料です恐れ入りますがこちらの商品は「お一人様一回限り最大4ビンまで」のご注文とさせていただきます。",
        "itemUrl": "http://item.rakuten.co.jp/honeymother/umf10manuka-250g/",
        "affiliateUrl": "",
        "imageFlag": 1,
        "smallImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/honeymother/cabinet/manuka-umf/img61070761.jpg?_ex=64x64"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/honeymother/cabinet/manuka-umf/img60094898.jpg?_ex=64x64"
          }
        ],
        "mediumImageUrls": [
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/honeymother/cabinet/manuka-umf/img61070761.jpg?_ex=128x128"
          },
          {
            "imageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/honeymother/cabinet/manuka-umf/img60094898.jpg?_ex=128x128"
          }
        ],
        "availability": 1,
        "taxFlag": 0,
        "postageFlag": 0,
        "creditCardFlag": 1,
        "shopOfTheYearFlag": 0,
        "shipOverseasFlag": 0,
        "shipOverseasArea": "",
        "asurakuFlag": 0,
        "asurakuClosingTime": "",
        "asurakuArea": "",
        "affiliateRate": "1.0",
        "startTime": "",
        "endTime": "",
        "reviewCount": 5111,
        "reviewAverage": "4.57",
        "pointRate": 1,
        "pointRateStartTime": "",
        "pointRateEndTime": "",
        "shopName": "マヌカハニーのハニーマザー",
        "shopCode": "honeymother",
        "shopUrl": "http://www.rakuten.co.jp/honeymother/",
        "genreId": "507771"
      }
    },
    {
      "Item": {
        "rank": 14,
        "carrier": 0,
        "itemName": "【★目玉商品12／17まで】【送料無料】変身ベルト　DXゴース
```


### Product/Search

#### Description

Gets up to 30 products by keywords, genre or product id. Each product can be sold by one or multiple sellers and each shop can have a different price for them.
#### Resource URL

https://app.rakuten.co.jp/services/api/Product/Search/20140305
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
keyword<br>*Search keywords* | string | At least one is required | UTF-8 URL encoded string<br>The keyword parameter can have a maximum length of 128 single byte characters<br>The keyword parameter is delimited with single byte space characters. This defaults to an AND operation including all the keywords. To use OR instead set the orFlag to 1.<br>Each search keyword must be at least two single byte characters or one double byte character.<br>An exception is a minimum of two characters if the search keywords are using hiragana, katakana, or symbols.
genreId<br>*Genre ID* | string | At least one is required | ID to specify a genre in Rakuten Ichiba.
productId<br>*Product ID* | string | At least one is required | ID of the product.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.
page<br>*Result page* | integer | Optional | An integer between 1 and 100.
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
minPrice<br>*Minimum price* | long | Optional | An integer greater than 0 and less than 999,999,999
maxPrice<br>*Maximum price* | long | Optional | An integer greater than 0 and less than 999,999,999<br>maxPrice must be larger than minPrice.
orFlag<br>*OR search flag* | integer | Optional | Choose between AND searches and OR searches when there are multiple keywords.<br>*It isn't possible to use a complex search condition like "(A and B) or C".
genreInformationFlag<br>*Genre information flag* | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Product/Search/20140305?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=列車&hits=5
##### Response

```json
{
  "count": 2492,
  "page": 1,
  "first": 1,
  "last": 5,
  "hits": 5,
  "pageCount": 100,
  "Products": [
    {
      "Product": {
        "productId": "c6a423267274b6ae4fdba858dd1909a0",
        "productName": "アートディンク A列車で行こう9 Ver4.0 マスターズ コンプリートパック",
        "productNo": "",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/c6a423267274b6ae4fdba858dd1909a0/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/c6a423267274b6ae4fdba858dd1909a0/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/001/723/10010004988640001723_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/001/723/10010004988640001723_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "",
        "makerCode": "104988640",
        "makerName": "アートディンク",
        "makerNameKana": "アートデインク",
        "makerNameFormal": "株式会社アートディンク",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/211723/104988640/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/211723/104988640/",
        "itemCount": 15,
        "salesItemCount": 15,
        "usedExcludeCount": 15,
        "usedExcludeSalesItemCount": 15,
        "maxPrice": 19057,
        "salesMaxPrice": 19057,
        "usedExcludeMaxPrice": 19057,
        "usedExcludeSalesMaxPrice": 19057,
        "minPrice": 14790,
        "salesMinPrice": 14790,
        "usedExcludeMinPrice": 14790,
        "usedExcludeSalesMinPrice": 14790,
        "averagePrice": 17078,
        "reviewCount": 2,
        "reviewAverage": 4.5,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/c6a423267274b6ae4fdba858dd1909a0/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/c6a423267274b6ae4fdba858dd1909a0/review/",
        "rank": 13,
        "rankTargetGenreId": "211706",
        "rankTargetProductCount": 5248,
        "genreId": "211723",
        "genreName": "その他",
        "ProductDetails": []
      }
    },
    {
      "Product": {
        "productId": "fa5c46cab237a304b4d32b730bea7807",
        "productName": "アンパンマントロッコ DK-7127",
        "productNo": "DK-7127",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/fa5c46cab237a304b4d32b730bea7807/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/fa5c46cab237a304b4d32b730bea7807/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/971/404/308/664/10010004971404308664_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/971/404/308/664/10010004971404308664_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "",
        "makerCode": "104971404",
        "makerName": "アガツマ",
        "makerNameKana": "アガツマ",
        "makerNameFormal": "株式会社アガツマ",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/101198/104971404/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/101198/104971404/",
        "itemCount": 25,
        "salesItemCount": 18,
        "usedExcludeCount": 25,
        "usedExcludeSalesItemCount": 18,
        "maxPrice": 2669,
        "salesMaxPrice": 2298,
        "usedExcludeMaxPrice": 2669,
        "usedExcludeSalesMaxPrice": 2298,
        "minPrice": 1300,
        "salesMinPrice": 1300,
        "usedExcludeMinPrice": 1300,
        "usedExcludeSalesMinPrice": 1300,
        "averagePrice": 1884,
        "reviewCount": 1,
        "reviewAverage": 5,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/fa5c46cab237a304b4d32b730bea7807/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/fa5c46cab237a304b4d32b730bea7807/review/",
        "rank": 10169,
        "rankTargetGenreId": "207563",
        "rankTargetProductCount": 17707,
        "genreId": "101198",
        "genreName": "その他",
        "ProductDetails": []
      }
    },
    {
      "Product": {
        "productId": "94f5fffc35d5d45bc0c392d6e3d58f5e",
        "productName": "クイニーザップ ベビーカー イッパイツナゴウ EF200セット",
        "productNo": "",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/94f5fffc35d5d45bc0c392d6e3d58f5e/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/94f5fffc35d5d45bc0c392d6e3d58f5e/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/904/810/348/856/10010004904810348856_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/904/810/348/856/10010004904810348856_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "",
        "makerCode": "104904810",
        "makerName": "タカラトミー",
        "makerNameKana": "タカラトミー",
        "makerNameFormal": "株式会社タカラトミー",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/213553/104904810/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/213553/104904810/",
        "itemCount": 13,
        "salesItemCount": 4,
        "usedExcludeCount": 13,
        "usedExcludeSalesItemCount": 4,
        "maxPrice": 9490,
        "salesMaxPrice": 9490,
        "usedExcludeMaxPrice": 9490,
        "usedExcludeSalesMaxPrice": 9490,
        "minPrice": 2800,
        "salesMinPrice": 9074,
        "usedExcludeMinPrice": 2800,
        "usedExcludeSalesMinPrice": 9074,
        "averagePrice": 5753,
        "reviewCount": 1,
        "reviewAverage": 1,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/94f5fffc35d5d45bc0c392d6e3d58f5e/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/94f5fffc35d5d45bc0c392d6e3d58f5e/review/",
        "rank": 3176,
        "rankTargetGenreId": "551256",
        "rankTargetProductCount": 6862,
        "genreId": "213553",
        "genreName": "その他",
        "ProductDetails": [
          {
            "detail": {
              "name": "シリーズ名/愛称",
              "value": "プラレール"
            }
          },
          {
            "detail": {
              "name": "本体サイズ(H×W×D)mm",
              "value": "51×41×1120"
            }
          },
          {
            "detail": {
              "name": "対象年齢",
              "value": "3歳以上"
            }
          },
          {
            "detail": {
              "name": "使用乾電池",
              "value": "単2電池×1本(別売)"
            }
          }
        ]
      }
    },
    {
      "Product": {
        "productId": "11682ec5f5d5cad9c752cb799f973093",
        "productName": "めちゃモテ・サックスアルトサックス A列車で行こう",
        "productNo": "",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/11682ec5f5d5cad9c752cb799f973093/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/11682ec5f5d5cad9c752cb799f973093/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/218/866/361/10010004580218866361_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/218/866/361/10010004580218866361_1.jpg?_ex=128x128",
        "productCaption": "",
        "releaseDate": "2012年2月17日",
        "makerCode": "10458021886",
        "makerName": "ウィンズスコア",
        "makerNameKana": "ウインズスコア",
        "makerNameFormal": "株式会社ウィンズスコア",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/209332/10458021886/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/209332/10458021886/",
        "itemCount": 5,
        "salesItemCount": 5,
        "usedExcludeCount": 5,
        "usedExcludeSalesItemCount": 5,
        "maxPrice": 1080,
        "salesMaxPrice": 1080,
        "usedExcludeMaxPrice": 1080,
        "usedExcludeSalesMaxPrice": 1080,
        "minPrice": 1080,
        "salesMinPrice": 1080,
        "usedExcludeMinPrice": 1080,
        "usedExcludeSalesMinPrice": 1080,
        "averagePrice": 1080,
        "reviewCount": 0,
        "reviewAverage": 0,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/11682ec5f5d5cad9c752cb799f973093/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/11682ec5f5d5cad9c752cb799f973093/review/",
        "rank": 53068,
        "rankTargetGenreId": "209332",
        "rankTargetProductCount": 134669,
        "genreId": "209332",
        "genreName": "全般",
        "ProductDetails": []
      }
    },
    {
      "Product": {
        "productId": "673ba66b41abdc42e2c0be1091d58240",
        "productName": "A列車で行こう3D 3DS",
        "productNo": "CTRPAALJ",
        "brandName": "",
        "productUrlPC": "http://product.rakuten.co.jp/product/-/673ba66b41abdc42e2c0be1091d58240/",
        "productUrlMobile": "http://m.product.rakuten.co.jp/product/673ba66b41abdc42e2c0be1091d58240/",
        "affiliateUrl": null,
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/200/034/10010004988640200034_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/988/640/200/034/10010004988640200034_1.jpg?_ex=128x128",
        "productCaption": "鉄道会社の社長となり、都市開発を行うシリーズ最新作。列車や建物の種類が大幅に増加し、老朽化や主力資源、街並の変化など、時代の変遷を味わえる。",
        "releaseDate": "2014年02月13日",
        "makerCode": "104988640",
        "makerName": "アートディンク",
        "makerNameKana": "アートデインク",
        "makerNameFormal": "株式会社アートディンク",
        "makerPageUrlPC": "http://product.rakuten.co.jp/category/-/562905/104988640/",
        "makerPageUrlMobile": "http://m.product.rakuten.co.jp/category/562905/104988640/",
        "itemCount": 68,
        "salesItemCount": 33,
        "usedExcludeCount": 36,
        "usedExcludeSalesItemCount": 20,
        "maxPrice": 10890,
        "salesMaxPrice": 10890,
        "usedExcludeMaxPrice": 10890,
        "usedExcludeSalesMaxPrice": 10890,
        "minPrice": 3880,
        "salesMinPrice": 4082,
        "usedExcludeMinPrice": 3880,
        "usedExcludeSalesMinPrice": 4930,
        "averagePrice": 5207,
        "reviewCount": 18,
        "reviewAverage": 4.67,
        "reviewUrlPC": "http://product.rakuten.co.jp/product/-/673ba66b41abdc42e2c0be1091d58240/review/",
        "reviewUrlMobile": "http://m.product.rakuten.co.jp/product/673ba66b41abdc42e2c0be1091d58240/review/",
        "rank": 2174,
        "rankTargetGenreId": "553848",
        "rankTargetProductCount": 4870,
        "genreId": "562905",
        "genreName": "その他",
        "ProductDetails": [
          {
            "detail": {
              "name": "フリガナ",
              "value": "エーレッシャデイコウスリーディー"
            }
          },
          {
            "detail": {
              "name": "プラットフォーム",
              "value": "3DS"
            }
          },
          {
            "detail": {
              "name": "ジャンル",
              "value": "シミュレーション"
            }
          },
          {
            "detail": {
              "name": "テイスト",
              "value": "経営・鉄道"
            }
          },
          {
            "detail": {
              "name": "型番",
              "value": "CTRPAALJ"
            }
          },
          {
            "detail": {
              "name": "その他",
              "value": "ダウンロードコンテンツ対応"
            }
          },
          {
            "detail": {
              "name": "CEROレーティング",
              "value": "A 全年齢対象"
            }
          },
          {
            "detail": {
              "name": "プレイ人数",
              "value": "1人"
            }
          },
          {
            "detail": {
              "name": "ディレクター",
              "value": "飯塚正樹"
            }
          }
        ]
      }
    }
  ],
  "GenreInformation": {
    "parent": [],
    "current": [],
    "children": []
  }
}
```


## Rakuten Books

![Rakuten Books](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-ichiba.png)
* **Name** Rakuten Books
* **URL** http://books.rakuten.co.jp/
* **Description** Rakuten's shop for media products like books, magazines, videogames, DVDs, Blu-ray and software.

### BooksTotal/Search

#### Description

Gets up to 30 media items by keywords, genre or ISBN/JAN.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksTotal/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
keyword<br>*Search keywords* | string | At least one is required | UTF-8 URL encoded string<br>The keyword parameter can have a maximum length of 128 single byte characters<br>The keyword parameter is delimited with single byte space characters. This defaults to an AND operation including all the keywords. To use OR instead set the orFlag to 1.<br>Each search keyword must be at least two single byte characters or one double byte character.<br>An exception is a minimum of two characters if the search keywords are using hiragana, katakana, or symbols.
booksGenreId<br>*Book genre ID* | string | At least one is required | Book ID to specify a book genre.<br>Please use the Book Genre Search API to look up book genre names and genre relations.
isbnjan<br>*ISBN/JAN code* | string | At least one is required | Use a 13 character code by removing all the hyphen symbols.<br>(*1) If ISBN/JAN code is specified, please do not set the search keywords and book genre ID parameters.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30
page<br>*Result page* | integer | Optional | An integer between 1 and 100
availability<br>*Availability* | integer | Optional |
outOfStockFlag<br>*Out of Stock Flag* | integer | Optional |
chirayomiFlag<br>*Chira Yomi Flag* | integer | Optional |
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.
field<br>*Search field* | integer | Optional |
carrier<br>*Platform* | integer | Optional |
orFlag<br>*OR search flag* | integer | Optional | Choose between AND searches and OR searches when there are multiple keywords.<br>*It isn't possible to use a complex search condition like "(A and B) or C".
NGKeyword<br>*Excluded keywords (*3)* | string | Optional | Words to exclude from search results<br>Strings encoded with UTF-8 URL encoding<br>Same format as keyword<br>(*3) This field can only be used if the search keywords field is set.
genreInformationFlag<br>*Genre information flag* | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/BooksTotal/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=ドン・キホーテ&hits=3
##### Response

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


### BooksCD/Search

#### Description

Gets up to 30 CD items by title, artist, label, JAN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksCD/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
title<br>*Title* | string | At least one is required | Keywords to search from the title of the CD.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
artistName<br>*Artist Name* | string | At least one is required | Keywords to search from the artist's or composer's name.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
label<br>*Label* | string | At least one is required | Keywords to search from label releasing the items.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
jan<br>*CD JAN code* | long | At least one is required | Search for a JAN code associated to a CD.
bookGenreId<br>*Book genre ID* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 002 (CD) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page * | integer | Optional | An integer between 1 and 30.
page<br>*Result page  * | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional |
outOfStockFlag<br>*Out of Stock Flag  * | integer | Optional |
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

https://app.rakuten.co.jp/services/api/BooksCD/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&artistName=speed&hits=3
##### Response

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


### BooksDVD/Search

#### Description

Gets up to 30 DVD/Blu-ray items by title, artist, label, JAN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksDVD/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
title<br>*DVD/Blu-ray Title* | string | At least one is required | Keywords to search from the title of the DVD/Blu-ray.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
artistName<br>*Director's or Actor's Name* | string | At least one is required | Keywords to search from the director's or actor's name.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
label<br>*Label* | string | At least one is required | Keywords to search from label releasing the items.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
jan<br>*JAN* | long | At least one is required | Search for a JAN code associated to a DVD/Blu-ray.
bookGenreId<br>*Book genre ID* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 003 (DVD/Blu-ray) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.
page<br>*Result page* | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional |
outOfStockFlag<br>*Out of Stock Flag  * | integer | Optional |
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

https://app.rakuten.co.jp/services/api/BooksDVD/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&title=ワンピース&hits=3
##### Response

```json
{
  "count": 318,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 100,
  "Items": [
    {
      "Item": {
        "title": "ONE PIECE ワンピース 17THシーズン ドレスローザ編 PIECE.21",
        "titleKana": "ワンピース セブンティーンスシーズン ドレスローザヘン ピース 21",
        "artistName": "尾田栄一郎/田中真弓/久田和也",
        "artistNameKana": "オダエイイチロウ/タナカマユミ/クダカズヤ",
        "label": "エイベックス・ピクチャーズ(株)",
        "jan": "4562475257809",
        "makerCode": "EYBA-10780",
        "itemCaption": "",
        "salesDate": "2016年03月02日",
        "itemPrice": 3742,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13513755/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "003206001/003206002/003206003/003206004/003206005"
      }
    },
    {
      "Item": {
        "title": "ONE PIECE ワンピース 17THシーズン ドレスローザ編 PIECE.21【Blu-ray】",
        "titleKana": "ワンピース セブンティーンスシーズン ドレスローザヘン ピース 21",
        "artistName": "尾田栄一郎/田中真弓/久田和也",
        "artistNameKana": "オダエイイチロウ/タナカマユミ/クダカズヤ",
        "label": "エイベックス・ピクチャーズ(株)",
        "jan": "4562475257816",
        "makerCode": "EYXA-10781",
        "itemCaption": "",
        "salesDate": "2016年03月02日",
        "itemPrice": 4573,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13513754/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "003215007"
      }
    },
    {
      "Item": {
        "title": "ONE PIECE ワンピース 17THシーズン ドレスローザ編 PIECE.20",
        "titleKana": "ワンピース セブンティーンスシーズン ドレスローザヘン ピース 20",
        "artistName": "田中真弓/岡村明美/中井和哉",
        "artistNameKana": "タナカマユミ/オカムラアケミ/ナカイカズヤ",
        "label": "エイベックス・ピクチャーズ(株)",
        "jan": "4562475257533",
        "makerCode": "EYBA-10753",
        "itemCaption": "",
        "salesDate": "2016年02月03日",
        "itemPrice": 3742,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13471089/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "003206001/003206002/003206003/003206004/003206005"
      }
    }
  ],
  "GenreInformation": []
}
```


### BooksForeignBook/Search

#### Description

Gets up to 30 foreign book items by title, author, publisher, ISBN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksForeignBook/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
title<br>*Title* | string | At least one is required | Search for a book title.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
author<br>*Author* | string | At least one is required | Search for an author's name.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
publisherName<br>*Publisher name* | string | At least one is required | Search for a publisher.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
isbn<br>*Book ISBN code* | string | At least one is required | Search for a ISBN code (book code).
booksGenreId<br>*Book genre ID  * | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 005 (Foreign Book) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.
page<br>*Result page* | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional |
outOfStockFlag<br>*Out of Stock Flag  * | integer | Optional |
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

https://app.rakuten.co.jp/services/api/BooksForeignBook/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&author=cervantes&hits=3
##### Response

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
publisherName<br>*Publisher name  * | string | At least one is required | Search for a publisher.<br>This parameter must be UTF-8 encoded.<br>You can search multiple keywords separating them by a space.
jan<br>*Magazine JAN code* | long | At least one is required | Search for a magazine JAN code.
booksGenreId<br>*Book genre ID  * | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 007 (Magazines) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page * | integer | Optional | An integer between 1 and 30.
page<br>*Result page  * | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional |
outOfStockFlag<br>*Out of Stock Flag  * | integer | Optional |
chirayomiFlag<br>*Chira Yomi Flag * | integer | Optional |
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
genreInformationFlag<br>*Genre information flag * | integer | Optional |
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


### BooksSoftware/Search

#### Description

Gets up to 30 software items by title, OS, maker, label, JAN or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksSoftware/Search/20130522
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
title<br>*Software Title* | string | At least one is required | Keywords to search from the software title.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
os<br>*Supported OS* | string | At least one is required | Search for supported OS (operating system).<br>This string needs to be UTF-8 encoded.
makerCode<br>*MPN (Manufacturer Part Number)* | string | At least one is required | Search for MPN (Manufacturer Part Number).<br>This string needs to be UTF-8 encoded.
label<br>*Publisher name* | string | At least one is required | Keywords to search from publisher releasing the items.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.
jan<br>*Software JAN code* | long | At least one is required | Search for a software JAN code.
booksGenreId<br>*Book genre ID* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 004 (software) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.
page<br>*Result page* | integer | Optional | An integer between 1 and 100.
availability<br>*Availability* | integer | Optional |
outOfStockFlag<br>*Out of Stock Flag* | integer | Optional |
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.
carrier<br>*Platform* | integer | Optional |
genreInformationFlag<br>*Genre information flag * | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/BooksSoftware/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&os=mac&hits=3
##### Response

```json
{
  "count": 468,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 100,
  "Items": [
    {
      "Item": {
        "title": "BiND for WebLiFE 8 プロフェッショナル Macintosh 解説本付き",
        "titleKana": "バインド フォー ウェブライフ 8 プロフェッショナル マッキントッシュ カイセツボンツキ",
        "os": "Mac",
        "label": "",
        "jan": "4527956025056",
        "makerCode": "DSP-02505",
        "itemCaption": "PCもスマホもすぐさま、思いのままに。\n初めてでも自在にアレンジ。PCサイトを自動でスマホに最適化\n\nBiND は、HTMLやCSSなどの専門知識がなくてもデザイン性の高いウェブサイトが構築可能。\n高品質かつ豊富なテンプレートと特許取得の独自のブロック編集によって自在なカスタマイズ性が実現し、\nウェブ制作の初心者から作業効率を重視するプロのデザイナーに至るまで広く活用されています。\n多くのお客様からのご要望にお応えして「BiND8 解説本バンドル版」発売！\n\n※収録テンプレート数219サイト（WordPress、Facebookページ含む）\n※WebLiFE*サーバー ベーシックコース24ヶ月+プレミアムコース3ヶ月 無料\n※Smooth Contact プロコース（980円／月）1年間利用権付\n※BiND8ガイドブック 「BiND8の教科書」\n\n【レスポンシブWebへ対応】\nPCサイトをスマホサイトに自動で最適化。\n閲覧するデバイスのサイズに合わせて自動でレイアウトを最適表示する、レスポンシブ対応のWebサイトが作れるようになりました。\nレスポンシブ対応のテンプレート（全20種62カラーバリエ）を使って作る手軽さに加え、\nページの編集エリアを指す「ブロック」単位で表示の有無を設定できるため、PCとスマホとで情報量のコントロールも可能です。\n両サイトをプレビューしながら作れるため調整もしやすく便利です。\n\n【統制されたデザインで見やすさ倍増】\nCSS設定を一括で行える新機能「Dress」を搭載。Webデザインを制御するCSSを一括して設定可能。\n「Dress」機能では、カラー、フォント、余白などサイト全体に掛るCSS設定の入った20種のDressテンプレートから選べるほか、\nユーザーが任意に設定し保存することもできます。\nデザインカスタマイズする際にも、統制感をキープしながらアレンジしていくことができ、\nWebデザインに不慣れな方でもデザインが崩れにくく、情報の見やすいWebサイトが作れます。\n\n【高性能フォームを美しいデザインで】\nセキュリティ万全なフォーム「Smooth Contact」が始動。\nSSLに対応した、機能もデザインも高性能なフォームサービスが始まります。\n問い合わせ状況は専用の管理画面で確認でき、メール転送も可能な高性能なフォームサービスが、\n公開サーバーに関係なく、かつ無料で利用できる環境を用意しました。\nサイトデザインに合わせたオリジナルのフォームが実装可能となります。\n\n【BiNDの構造を抜本的に見直し、飛躍的に進化】\n操作UIを刷新！ユーザビリティを大きく向上\nこれまでのリッチインターフェースから、シンプルな見た目に一新し、あらゆる基本編集機能を改善。\nよく使う機能をより使いやすく、作業パフォーマンスが向上します。\nBiNDのサイト制作で要となるブロック編集の最小単位「ブロック」のコピー機能や、\n作成したページを別サイトにも移行できる機能のほか、検索機能が充実しました。",
        "salesDate": "2015年12月18日",
        "itemPrice": 33264,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13517578/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "004319007007"
      }
    },
    {
      "Item": {
        "title": "Tri-folding Bluetooth Keyboard シャンパンゴールド GK930-CG",
        "titleKana": "トリホールディング ブルートゥース キーボード シャンパンゴールド",
        "os": "Mac",
        "label": "",
        "jan": "4582159571342",
        "makerCode": "GK930-CG",
        "itemCaption": "●スマホやタブレットに最適！折り畳み式Bluetoothキーボード\n・三つ折りタイプだから実現できた、コンパクトながらもワイドで使いやすい設計\n・場所を問わずいつでもどこでもスマホやタブレットでのタイピングが快適に\n・Bluetoothは端末と一度ペアリングしておけば次回以降、電源ONで自動的に接続\n\n●抜群の打ちやすさで快適なタイピングを実現\n・17.5mmのワイドなキーピッチ、1.8mmのキーストロークで快適にタイピング可能\n・シームレス構造により、折り畳み部分のつなぎ目を気にせずタイピング可能\n\n●使いやすさにこだわった設計\n・本体背面のアルミ素材により、デザイン性だけでなく軽量化も実現\n・キーボードの開閉で電源が自動でON／OFFになるオートウェイク機能搭載\n\n●マルチOS対応！タブレットもスマホもOSを問わずこれ1台でOK\n・各OSに対応したファンクションキーを搭載、ボタン一つでOSモードの切換が可能\n・日本語配列に対応する記号キーを別色で印字！iOSは勿論、AndroidやWindowsでもOSによる配列認識を気にせずタイピング可能\n\n●軽量コンパクト設計で持ち運びに最適\n・重量は310g、収納時のサイズは149mm×100mmと持ち運びに便利な軽量コンパクト設計\n・乾電池ではなくリチウムイオンバッテリー内蔵のため薄型設計を実現\n・2時間の充電で約60時間の連続使用が可能、一度の充電だけで長期間使用もOK\n\n●対応OS：Windows 8〜8.1／Android OS4.1以降／iOS6以降　\n●キータイプ：パンタグラフ　\n●キー配列：64キー（英語配列）　\n●キーピッチ： 17.5mm ／ キーストローク：1.8mm　\n●サイズ（使用時）：252×92×10mm ／ サイズ（収納時）：145×92×18mm \n●本体重量：184g　\n●USBインターフェース：Micro USB　\n●電源：リチウムイオン電池（内臓）　\n●充電時間：約2時間 ／ 連続使用時間：約65時間 ／ 待受時間：約100日間\n●接続方式： Bluetooth Ver. 3.0　\n●接続距離：10m　\n●製品内容：Bluetoothワイヤレスキーボード、USBケーブル（キーボード充電用）、ユーザーガイド、製品保証書（保証期間：1年）\n※本製品は技適（TELEC）認証を取得しています",
        "salesDate": "2015年12月25日",
        "itemPrice": 10778,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13517547/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "004322002"
      }
    },
    {
      "Item": {
        "title": "BiND for WebLiFE 8 スタンダード Macintosh 解説本付き",
        "titleKana": "バインド フォー ウェブライフ 8 スタンダード マッキントッシュ カイセツボンツキ",
        "os": "Mac",
        "label": "",
        "jan": "4527956024059",
        "makerCode": "DSP-02405",
        "itemCaption": "初めてでも自在にアレンジ。PCサイトを自動でスマホに最適化\n\nBiND は、HTMLやCSSなどの専門知識がなくてもデザイン性の高いウェブサイトが構築可能。\n高品質かつ豊富なテンプレートと特許取得の独自のブロック編集によって自在なカスタマイズ性が実現し、\nウェブ制作の初心者から作業効率を重視するプロのデザイナーに至るまで広く活用されています。\n多くのお客様からのご要望にお応えして「BiND8 解説本バンドル版」発売！\n\n※収録テンプレート数180サイト\n※WebLiFE*サーバー ベーシックコース6ヶ月 無料\n※Smooth Contact フリーコースが利用可能\n※BiND8ガイドブック 「BiND8の教科書」\n\n【レスポンシブWebへ対応。伝わりやすいWebへ】\nPCサイトをスマホサイトに自動で最適化。\n閲覧するデバイスのサイズに合わせて自動でレイアウトを最適表示する、レスポンシブ対応のWebサイトが作成できる！\nレスポンシブ対応のテンプレート（全20種62カラーバリエ）を使って作る手軽さに加え、\nページの編集エリアを指す「ブロック」単位で表示の有無を設定できるため、PCとスマホとで情報量のコントロールも可能。\n両サイトをプレビューしながら作れるため調整もしやすく便利です。\n\n【統制されたデザインで見やすさ倍増】\nCSS設定を一括で行える新機能「Dress」を搭載。Webデザインを制御するCSSを一括して設定可能。\n「Dress」機能では、カラー、フォント、余白などサイト全体に掛るCSS設定の入った20種のDressテンプレートから選べるほか、\nユーザーが任意に設定し保存することもできます。\nデザインカスタマイズする際にも、統制感をキープしながらアレンジしていくことができ、\nWebデザインに不慣れな方でもデザインが崩れにくく、情報の見やすいWebサイトが作れます。\n\n【高性能フォームを美しいデザインで】\nセキュリティ万全なフォーム「Smooth Contact」が始動。\nSSLに対応した、機能もデザインも高性能なフォームサービスが始まります。\n問い合わせ状況は専用の管理画面で確認でき、メール転送も可能な高性能なフォームサービスが、\n公開サーバーに関係なく、かつ無料で利用できる環境を用意。\nサイトデザインに合わせたオリジナルのフォームが実装可能。\n\n【BiNDの構造を抜本的に見直し、飛躍的に進化】\n操作UIを刷新！ユーザビリティを大きく向上\nBiNDが登場して以来初となる、ユーザーインターフェースを刷新。\nこれまでのリッチインターフェースから、シンプルな見た目に一新し、あらゆる基本編集機能の改善を図りました。\nよく使う機能をより使いやすく、作業パフォーマンスが向上します。\nBiNDのサイト制作で要となるブロック編集の最小単位「ブロック」のコピー機能や、\n作成したページを別サイトにも移行できる機能のほか、検索機能が充実。",
        "salesDate": "2015年12月18日",
        "itemPrice": 22464,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13517577/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "004319007007"
      }
    }
  ],
  "GenreInformation": []
}
```


### BooksGenre/Search

#### Description

Gets a media genre's attributes, children genres and ancestor genres by genre id.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksGenre/Search/20121128
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
booksGenreId<br>*Book genre ID* | string | Required | Genre ID to get information from.<br>Root booksGenreId is <code>000</code>.
genrePath<br>*Genre path* | integer | Optional | Whether to include ancestor genres or not in the response.<br>0: do not include ancestors<br>1: include ancestors
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/BooksGenre/Search/20121128?applicationId=REPLACE_WITH_YOUR_APP_ID&booksGenreId=001
##### Response

```json
{
  "current": {
    "booksGenreId": "001",
    "booksGenreName": "本",
    "genreLevel": 1
  },
  "children": [
    {
      "child": {
        "booksGenreId": "001001",
        "booksGenreName": "漫画（コミック）",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001002",
        "booksGenreName": "語学・学習参考書",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001003",
        "booksGenreName": "絵本・児童書・図鑑",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001004",
        "booksGenreName": "小説・エッセイ",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001005",
        "booksGenreName": "パソコン・システム開発",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001006",
        "booksGenreName": "ビジネス・経済・就職",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001007",
        "booksGenreName": "旅行・留学・アウトドア",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001008",
        "booksGenreName": "人文・思想・社会",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001009",
        "booksGenreName": "ホビー・スポーツ・美術",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001010",
        "booksGenreName": "美容・暮らし・健康・料理",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001011",
        "booksGenreName": "エンタメ・ゲーム",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001012",
        "booksGenreName": "科学・医学・技術",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001013",
        "booksGenreName": "写真集・タレント",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001016",
        "booksGenreName": "資格・検定",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001017",
        "booksGenreName": "ライトノベル",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001018",
        "booksGenreName": "楽譜",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001019",
        "booksGenreName": "文庫",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001020",
        "booksGenreName": "新書",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001021",
        "booksGenreName": "ボーイズラブ（BL）",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001022",
        "booksGenreName": "付録付き",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001023",
        "booksGenreName": "バーゲン本",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001025",
        "booksGenreName": "コミックセット",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001026",
        "booksGenreName": "カレンダー・手帳・家計簿",
        "genreLevel": 2
      }
    }
  ],
  "parents": []
}
```


## Rakuten Bookmark

![Rakuten Bookmark](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-ichiba.png)
* **Name** Rakuten Bookmark
* **URL** http://my.bookmark.rakuten.co.jp/
* **Description** Rakuten's service for allowing users to make list of their favorite items.

### FavoriteBookmark/List

#### Description

Gets up to 40 favorite bookmarks from the user performing the API call.
#### Resource URL

https://app.rakuten.co.jp/services/api/FavoriteBookmark/List/20120627
#### Resource Information

* **Auth Type** OAuth
* **OAuth Scope** Gets up to 40 favorite bookmarks from the user performing the API call.
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
page<br>*Page number* | integer | Optional | Starting number of the page to get
hits<br>*Number of results* | integer | Optional | Items per page. Maximum: 40.
sort<br>*Sort* | string | Optional | * In the case of the same registration date and time and the same price, the order cannot be predicted.
ispublic<br>*Only get public items* | string | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/FavoriteBookmark/List/20120627?access_token=REPLACE_WITH_THE_USER_ACCESS_TOKEN
##### Response

```json
{
  "summary": {
    "count": 2,
    "hits": 1,
    "pageCount": 2
  },
  "items": [
    {
      "item": {
        "bookmarkId": "4857547",
        "itemCode": "",
        "productId": "7e9f338152a7cf385b990611358ebd77",
        "shopName": "商品価格ナビ",
        "shopUrl": "http://product.rakuten.co.jp/",
        "itemName": "ねんどろいど チノ グッドスマイルカンパニー",
        "itemUrl": "http://product.rakuten.co.jp/product/-/7e9f338152a7cf385b990611358ebd77/",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/416/900/522/10010004580416900522_1.jpg?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/ran/img/1001/0004/580/416/900/522/10010004580416900522_1.jpg?_ex=128x128",
        "reviewCount": 0,
        "reviewUrl": "",
        "pointRate": 0,
        "reviewAverage": "",
        "postageFlag": 99,
        "taxFlag": 0,
        "affiliateUrl": ""
      }
    }
  ]
}
```


### FavoriteBookmark/Add

#### Description

Adds an item to the favorite bookmarks of the user performing the API call.
#### Resource URL

https://app.rakuten.co.jp/services/api/FavoriteBookmark/Add/20120627
#### Resource Information

* **Auth Type** OAuth
* **OAuth Scope** Adds an item to the favorite bookmarks of the user performing the API call.
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
itemCode<br>*Item Code* | string | Required | Please use the Rakuten Ichiba item code attribute from the search API.<br>Bookmarks can only be added to Rakuten Ichiba items.<br>Bookmarks cannot be added to Rakuten products.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/FavoriteBookmark/Add/20120627?access_token=REPLACE_WITH_THE_USER_ACCESS_TOKEN&itemCode=auc-choax2:10003154
##### Response

```json
{
  "bookmarkId": "4871095",
  "registDatetime": "2015/12/13 23:30:46"
}
```


### FavoriteBookmark/Delete

#### Description

Deletes a favorite bookmark from the user performing the API call.
#### Resource URL

https://app.rakuten.co.jp/services/api/FavoriteBookmark/Delete/20120627
#### Resource Information

* **Auth Type** OAuth
* **OAuth Scope** Deletes a favorite bookmark from the user performing the API call.
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
bookmarkId<br>*Bookmark ID* | string | Required | Bookmark ID to be deleted.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/FavoriteBookmark/Delete/20120627?access_token=REPLACE_WITH_THE_USER_ACCESS_TOKEN&bookmarkId=4857547
##### Response

```json
{
  "affectedCount": 1
}
```


## Rakuten Travel

![Rakuten Travel](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-travel.png)
* **Name** Rakuten Travel
* **URL** http://travel.rakuten.co.jp/
* **Description** Rakuten's travel reservation website.

### Travel/SimpleHotelSearch

#### Description

Gets up to 30 hotels by area class code, hotel number or coordinates.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/SimpleHotelSearch/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
largeClassCode<br>*Large class code* | string | At least one is required | Code specifying the country.<br>Please get this value from the GetAreaClass API.
middleClassCode<br>*Middle class code* | string | At least one is required | Code specifying the prefecture.<br>Please get this value from the GetAreaClass API.
smallClassCode<br>*Small class code* | string | At least one is required | Code specifying the city.<br>Please get this value from the GetAreaClass API.
detailClassCode<br>*Detail class code* | string | At least one is required | Code specifying stations or areas.<br>Please get this value from the GetAreaClass API.
hotelNo<br>*Hotel Number* | integer | At least one is required | Hotel number.<br>This field allows you to specify up to 15 numbers (using commas as separator).<br>Example: <code>hotelNo=12345,54321</code>
latitude<br>*Latitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example: <code>128,216.17</code><br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example: <code>35.6065914</code>
longitude<br>*Longitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example: <code>503,259.29</code><br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example: <code>139.7513225</code>
searchRadius<br>*Search Radius* | integer | Optional | Distance in km around latitude and longitude search.<br>Please set a value between 0.1 and 3.0.
squeezeCondition<br>*Narrowing Conditions* | string | Optional | This field allows you to specify more than one, using commas as separator.<br>Example: a non smoking room in hot spring inn: <code>squeezeCondition=kinen,onsen</code>
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.
page<br>*Result page* | integer | Optional | Number of page.<br>Integer between 1 and 100.<br>* 1) If the allReturnFlag was specified by the latitude and longitude search,
hits<br>*How many results per page* | integer | Optional | Parameters that determines the number of results per page.<br>Integer from 1 to 30.<br>(* 1) If the allReturnFlag was specified by the latitude and longitude search,<br>page and the hits parameters will not be used.
hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.
responseType<br>*Response Type* | string | Optional | Specify the amount of information returned in the response:
sort<br>*Sort* | string | Optional | (* 1) About "recommended order":<br>- In case of a search by facility number,<br>standard: facilities numerical order<br>- In case of search by longitude and latitude,<br>standard: order closest to farest from the specified coordinates
allReturnFlag<br>*All return flag* | integer | Optional | Flag for returning all results. (* 1) (* 2)<br>1: return all results<br>(* 1) only valid for latitude and longitude search.<br>(* 2) If the allReturnFlag has been specified, page hits and is disabled.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Travel/SimpleHotelSearch/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID&latitude=125994.28&longitude=488781.51&hits=3
##### Response

```json
{
  "pagingInfo": {
    "recordCount": 154,
    "pageCount": 52,
    "page": 1,
    "first": 1,
    "last": 3
  },
  "hotels": [
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 136197,
            "hotelName": "葵　KYOTO　STAY",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/dQ4dX/?f_no=136197",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/cHNRi/?f_no=136197&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/TDZXm/?noTomariHotel=136197",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/RmfmX/?f_hotel_no=136197",
            "hotelKanaName": "あおい　きょうと　すてい",
            "hotelSpecial": "川面のきらめく光。選び抜かれた骨董が古き良き時代へ誘います。ライブラリーで読書、川床テラスでお茶を。",
            "hotelMinCharge": 14800,
            "latitude": 125994.28,
            "longitude": 488781.51,
            "postalCode": "600-8013",
            "address1": "京都府",
            "address2": "京都市下京区木屋町通仏光寺上る天王町145-1 (オフィス)※町家は別の場所になります。",
            "telephoneNo": "075-354-7770",
            "faxNo": "075-354-7772",
            "access": "京阪「清水五条駅」徒歩5分/阪急「河原町駅」、京阪「祇園四条駅」徒歩10分/ＪＲ「京都駅」タクシーで10分",
            "parkingInformation": "無し：お近くのコインパーキングをご案内致します。",
            "nearestStation": null,
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136197/136197.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/136197.jpg",
            "roomImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136197/136197_1f.jpg",
            "roomThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/INTERIOR/136197.jpg",
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136197/136197map.gif",
            "reviewCount": null,
            "reviewAverage": null,
            "userReview": null
          }
        },
        {
          "hotelRatingInfo": {
            "serviceAverage": null,
            "locationAverage": null,
            "roomAverage": null,
            "equipmentAverage": null,
            "bathAverage": null,
            "mealAverage": null
          }
        }
      ]
    },
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 147867,
            "hotelName": "葵　ＨＯＴＥＬ　ＫＹＯＴＯ",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/dQ4dX/?f_no=147867",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/cHNRi/?f_no=147867&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/TDZXm/?noTomariHotel=147867",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/RmfmX/?f_hotel_no=147867",
            "hotelKanaName": "あおい　ほてる　きょうと",
            "hotelSpecial": "京都の伝統と革新。そして旅の喜びと癒し。ユニークでここにしかないラグジュアリーホテルが鴨川沿いに誕生",
            "hotelMinCharge": 14000,
            "latitude": 125994.03,
            "longitude": 488781.43,
            "postalCode": "600-8013",
            "address1": "京都府",
            "address2": "京都市下京区木屋町通仏光寺上る天王町146",
            "telephoneNo": "075-354-7770",
            "faxNo": "075-354-7772",
            "access": "阪急　河原町駅より徒歩",
            "parkingInformation": "無し",
            "nearestStation": "河原町（京都）",
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/147867/147867.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/147867.jpg",
            "roomImageUrl": null,
            "roomThumbnailUrl": null,
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/147867/147867map.gif",
            "reviewCount": null,
            "reviewAverage": null,
            "userReview": null
          }
        },
        {
          "hotelRatingInfo": {
            "serviceAverage": null,
            "locationAverage": null,
            "roomAverage": null,
            "equipmentAverage": null,
            "bathAverage": null,
            "mealAverage": null
          }
        }
      ]
    },
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 136898,
            "hotelName": "京乃宿　はなしおり",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/dQ4dX/?f_no=136898",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/cHNRi/?f_no=136898&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/TDZXm/?noTomariHotel=136898",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/hs/RmfmX/?f_hotel_no=136898",
            "hotelKanaName": "きょうのやど　はなしおり",
            "hotelSpecial": "【２０１２年3月オープン】一日一組様貸しきり高瀬川沿いのお宿。お宿までお届けの朝食付でごゆっくり♪",
            "hotelMinCharge": 9000,
            "latitude": 125993.63,
            "longitude": 488780.05,
            "postalCode": "600-8018",
            "address1": "京都府",
            "address2": "京都市下京区西木屋町仏光寺上がる市之町260-19",
            "telephoneNo": "090-5063-1500",
            "faxNo": "075-592-3596",
            "access": "阪急　河原町駅　京都マルイ出口2番　又は　木屋町南出入口1番より徒歩にて３分／京阪　祇園四条駅　出口3番より徒歩にて５分",
            "parkingInformation": "契約駐車場　1台あり　(一日料金2000円、前日までに要予約)",
            "nearestStation": "河原町（京都）",
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136898/136898.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/136898.jpg",
            "roomImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136898/136898_wa.jpg",
            "roomThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/INTERIOR/136898.jpg",
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136898/136898map.gif",
            "reviewCount": 33,
            "reviewAverage": 4.91,
            "userReview": null
          }
        },
        {
          "hotelRatingInfo": {
            "serviceAverage": 0,
            "locationAverage": 0,
            "roomAverage": 0,
            "equipmentAverage": 0,
            "bathAverage": 0,
            "mealAverage": 0
          }
        }
      ]
    }
  ]
}
```


### Travel/HotelDetailSeach

#### Description

Gets a hotel details by hotel number.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/HotelDetailSearch/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
hotelNo<br>*Hotel Number* | integer | Required | Hotel number from Rakuten Travel API.
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.
hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.
responseType<br>*Response Type* | string | Optional | Specify the amount of information returned in the response:
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Travel/HotelDetailSearch/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID&hotelNo=136197
##### Response

```json
{
  "hotels": [
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 136197,
            "hotelName": "葵　KYOTO　STAY",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/if/uPw0Q/?f_no=136197",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/if/ZwI4Q/?f_no=136197&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/if/G02wZ/?noTomariHotel=136197",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/if/50xNk/?f_hotel_no=136197",
            "hotelKanaName": "あおい　きょうと　すてい",
            "hotelSpecial": "川面のきらめく光。選び抜かれた骨董が古き良き時代へ誘います。ライブラリーで読書、川床テラスでお茶を。",
            "hotelMinCharge": 14800,
            "latitude": 125994.28,
            "longitude": 488781.51,
            "postalCode": "600-8013",
            "address1": "京都府",
            "address2": "京都市下京区木屋町通仏光寺上る天王町145-1 (オフィス)※町家は別の場所になります。",
            "telephoneNo": "075-354-7770",
            "faxNo": "075-354-7772",
            "access": "京阪「清水五条駅」徒歩5分/阪急「河原町駅」、京阪「祇園四条駅」徒歩10分/ＪＲ「京都駅」タクシーで10分",
            "parkingInformation": "無し：お近くのコインパーキングをご案内致します。",
            "nearestStation": null,
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136197/136197.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/136197.jpg",
            "roomImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136197/136197_1f.jpg",
            "roomThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/INTERIOR/136197.jpg",
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/136197/136197map.gif",
            "reviewCount": null,
            "reviewAverage": null,
            "userReview": null
          }
        },
        {
          "hotelRatingInfo": {
            "serviceAverage": null,
            "locationAverage": null,
            "roomAverage": null,
            "equipmentAverage": null,
            "bathAverage": null,
            "mealAverage": null
          }
        }
      ]
    }
  ]
}
```


### Travel/VacantHotelSearch

#### Description

Gets up to 30 vacant hotels for a specified checkin and checkout dates by area class code, hotel number or coordinates.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/VacantHotelSearch/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
largeClassCode<br>*Large class code* | string | At least one is required | Code specifying the country.<br>Please get this value from the GetAreaClass API.
middleClassCode<br>*Middle class code* | string | At least one is required | Code specifying the prefecture.<br>Please get this value from the GetAreaClass API.
smallClassCode<br>*Small class code* | string | At least one is required | Code specifying the city.<br>Please get this value from the GetAreaClass API.
detailClassCode<br>*Detail class code* | string | At least one is required | Code specifying stations or areas.<br>Please get this value from the GetAreaClass API.
hotelNo<br>*Hotel Number* | integer | At least one is required | Hotel number.<br>This field allows you to specify up to 15 numbers (using commas as separator).<br>Example: hotelNo=12345,54321
checkinDate<br>*Check-in date* | date | Required | YYYY-MM-DD
checkoutDate<br>*Check-out date* | date | Required | YYYY-MM-DD
adultNum<br>*Number of people (adults)* | integer | Optional | Integer between 1 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
upClassNum<br>*Number of people (elementary school upper grades)* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
lowClassNum<br>*Number of people (elementary school lower grades)* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
infantWithMBNum<br>*Number of people (young children (with food and bedding))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
infantWithMNum  <br>*Number of people (young children (meal only))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
infantWithBNum<br>*Number of people (young children (bedding only))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
infantWithoutMBNum<br>*Number of people (young children (food and bedding required))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
roomNum<br>*Number of rooms* | integer | Optional | Integer from 1 to 10.
maxCharge <br>*Maximum price* | long | Optional | Integer from 0 to 999999999.
minCharge<br>*Minimum price* | long | Optional | Integer from 0 to 999999999.<br>maxCharge must be greater than minCharge.
latitude<br>*Latitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example) 128,216.17<br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example) 35.6065914
longitude<br>*Longitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example) 503,259.29<br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example) 139.7513225
searchRadius<br>*Search Radius* | integer | Optional | Distance in km around latitude and longitude search.<br>Please set a value between 0.1 and 3.0.
squeezeCondition<br>*Narrowing Conditions* | string | Optional | This field allows you to specify more than one, using commas as separator.<br>Example: a non smoking room in hot spring inn: <code>squeezeCondition=kinen,onsen</code>
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.
hits<br>*How many results per page  * | integer | Optional | Parameters that determines the number of results per page.<br>Integer from 1 to 30.<br>(* 1) If the allReturnFlag was specified by the latitude and longitude search, page and the hits parameters will not be used.
page<br>*Result page  * | integer | Optional | Number of page.<br>Integer between 1 and 100.<br>* 1) If the allReturnFlag was specified by the latitude and longitude search,
searchPattern<br>*Search pattern* | integer | Optional | Parameter to specify the search pattern
hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.
responseType<br>*Response Type  * | string | Optional | Specify the amount of information returned in the response:
sort<br>*Sort* | string | Optional |
allReturnFlag<br>*All return flag * | integer | Optional | Flag for all cases return the information corresponding to the condition. (* 1) (* 2)<br>1: Return all results<br>(* 1) in the latitude and longitude search, responseType is small. It is only available when searchPattern is 0.<br>(* 2) If the page and hits has been specified, allReturnFlag is disabled.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Travel/VacantHotelSearch/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID&latitude=125994.28&longitude=488781.51&checkinDate=2016-06-24&checkoutDate=2016-06-29&hits=3
##### Response

```json
{
  "pagingInfo": {
    "recordCount": 22,
    "pageCount": 8,
    "page": 1,
    "first": 1,
    "last": 3
  },
  "hotels": [
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 147994,
            "hotelName": "ベッセルホテルカンパーナ京都五条",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/pvonD/?f_no=147994",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/vFumt/?f_no=147994&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/WzozX/?noTomariHotel=147994",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/gJNfM/?f_hotel_no=147994",
            "hotelKanaName": "べっせるほてるかんぱーなきょうとごじょう",
            "hotelSpecial": "２０１５年９月オープン！京都駅より地下鉄利用で約６分、四条からも徒歩圏内。サウナ付大浴場を備える。",
            "hotelMinCharge": 3375,
            "latitude": 125973.63,
            "longitude": 488750.7,
            "postalCode": "600-8180",
            "address1": "京都府",
            "address2": "京都市下京区東洞院通五条下る下万寿寺町498",
            "telephoneNo": "075-353-1000",
            "faxNo": "075-353-1001",
            "access": "市営地下鉄烏丸線「五条駅」３番出口より徒歩にて約１分",
            "parkingInformation": "先着順 立体駐車場32台 高さ1.55ｍ/23台　1.8ｍ/9台　1泊1500円（14時～11時）　",
            "nearestStation": "五条（京都市営）",
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/147994/147994.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/147994.jpg",
            "roomImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/147994/147994_kan1.jpg",
            "roomThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/INTERIOR/147994.jpg",
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/147994/147994map.gif",
            "reviewCount": 58,
            "reviewAverage": 3.95,
            "userReview": "またぜひ利用し…　2015-12-11 20:45:08投稿 <a href=\"http://img.travel.rakuten.co.jp/image/tr/api/re/gJNfM/?f_hotel_no=147994\" class=\"3click\">つづきはこちら</a>"
          }
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "s2",
                "roomName": "【建物側】スタンダードシングル☆禁煙",
                "planId": 3526180,
                "planName": "【60歳以上限定】シニアプラン☆素泊まり",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 0,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=147994&f_syu=s2&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=3526180",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 7650,
                "total": 7650,
                "chargeFlag": 0
              }
            }
          ]
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "s1",
                "roomName": "【建物側】スタンダードシングル★喫煙",
                "planId": 3526180,
                "planName": "【60歳以上限定】シニアプラン☆素泊まり",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 0,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=147994&f_syu=s1&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=3526180",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 7650,
                "total": 7650,
                "chargeFlag": 0
              }
            }
          ]
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "s2",
                "roomName": "【建物側】スタンダードシングル☆禁煙",
                "planId": 3526128,
                "planName": "連泊エコプラン☆素泊まり",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 0,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=147994&f_syu=s2&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=3526128",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 8200,
                "total": 8200,
                "chargeFlag": 0
              }
            }
          ]
        }
      ]
    },
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 10846,
            "hotelName": "コープ・イン・京都",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/pvonD/?f_no=10846",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/vFumt/?f_no=10846&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/WzozX/?noTomariHotel=10846",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/gJNfM/?f_hotel_no=10846",
            "hotelKanaName": "こーぷ・いん・きょうと",
            "hotelSpecial": "コープイン京都はみなさまの「なごみ・かたらい・人とひと」の感動をお手伝いするホテルです。",
            "hotelMinCharge": 3600,
            "latitude": 126013.16,
            "longitude": 488761.2,
            "postalCode": "604-8113",
            "address1": "京都府",
            "address2": "京都市中京区柳馬場通蛸薬師上ル井筒屋町４１１",
            "telephoneNo": "075-256-6600",
            "faxNo": "075-251-0120",
            "access": "地下鉄四条駅・烏丸御池駅・阪急烏丸駅より徒歩約１０分・ＪＲ京都駅よりタクシーで約１０分",
            "parkingInformation": "有料（1500円／1日）にて６台分あり（お電話等で必ずご予約ください）。",
            "nearestStation": "烏丸",
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/10846/10846.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/10846.jpg",
            "roomImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/10846/10846_sgl.jpg",
            "roomThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/INTERIOR/10846.jpg",
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/10846/10846map.gif",
            "reviewCount": 1689,
            "reviewAverage": 4.23,
            "userReview": "連休前の京都で良く空いていた。　2015-12-05 17:23:00投稿"
          }
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "nosmokings",
                "roomName": "＜大学生協組合員限定＞シングルルーム【禁煙】",
                "planId": 2648653,
                "planName": "≪大学生協組合員様限定≫京都をのんびり散策！！　市バス1日券付プラン",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 0,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=10846&f_syu=nosmokings&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=2648653",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 6000,
                "total": 6000,
                "chargeFlag": 0
              }
            }
          ]
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "nosmokings",
                "roomName": "＜大学生協組合員限定＞シングルルーム【禁煙】",
                "planId": 2626309,
                "planName": "【大学生協組合員様限定】当館人気★京のおばんざい朝食付ご宿泊プラン",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 1,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=10846&f_syu=nosmokings&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=2626309",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 6200,
                "total": 6200,
                "chargeFlag": 0
              }
            }
          ]
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "nosmokings",
                "roomName": "＜大学生協組合員限定＞シングルルーム【禁煙】",
                "planId": 2645696,
                "planName": "【大学生協組合員様限定】京都を楽々散策！！　市バス1日券＆朝食付プラン",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 1,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=10846&f_syu=nosmokings&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=2645696",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 6500,
                "total": 6500,
                "chargeFlag": 0
              }
            }
          ]
        }
      ]
    },
    {
      "hotel": [
        {
          "hotelBasicInfo": {
            "hotelNo": 145279,
            "hotelName": "ホテルグランバッハ京都",
            "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/pvonD/?f_no=145279",
            "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/vFumt/?f_no=145279&f_flg=PLAN",
            "dpPlanListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/WzozX/?noTomariHotel=145279",
            "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/gJNfM/?f_hotel_no=145279",
            "hotelKanaName": "ぐらんばっはきょうと",
            "hotelSpecial": "かくれ家に広がる、もうひとつの京都。京都のみやびな趣を感じながら過ごす、ちょっと贅沢な寛ぎのホテルステイをお届けします。",
            "hotelMinCharge": 4557,
            "latitude": 126001.17,
            "longitude": 488767.2,
            "postalCode": "600-8004",
            "address1": "京都府",
            "address2": "京都市下京区四条通寺町西入奈良物町363",
            "telephoneNo": "075-221-2211",
            "faxNo": "075-221-2214",
            "access": "ホテル入口は四条通添いマツキヨ角を曲がり２０ｍ程、麩屋町通側にございます（四条通側ではありませんのでご注意ください）。",
            "parkingInformation": "なし",
            "nearestStation": "河原町（京都）",
            "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/145279/145279.jpg",
            "hotelThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/90/145279.jpg",
            "roomImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/145279/145279_room.jpg",
            "roomThumbnailUrl": "http://img.travel.rakuten.co.jp/HIMG/INTERIOR/145279.jpg",
            "hotelMapImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/145279/145279map.gif",
            "reviewCount": 224,
            "reviewAverage": 4.32,
            "userReview": "夜の無料お茶漬けが美味しかったです。　2015-11-30 21:19:59投稿"
          }
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "dbl",
                "roomName": "禁煙　ダブルルーム",
                "planId": 3296366,
                "planName": "【正規料金】　素泊りプラン",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 0,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=145279&f_syu=dbl&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=3296366",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 22000,
                "total": 22000,
                "chargeFlag": 0
              }
            }
          ]
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "dbl",
                "roomName": "禁煙　ダブルルーム",
                "planId": 3296491,
                "planName": "【正規料金】　朝食付きプラン",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 1,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=145279&f_syu=dbl&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=3296491",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 23836,
                "total": 23836,
                "chargeFlag": 0
              }
            }
          ]
        },
        {
          "roomInfo": [
            {
              "roomBasicInfo": {
                "roomClass": "twn",
                "roomName": "【雅-みやび-】禁煙ツインルーム(ハリウッドツイン)",
                "planId": 3296366,
                "planName": "【正規料金】　素泊りプラン",
                "pointRate": 1,
                "withDinnerFlag": 0,
                "dinnerSelectFlag": 0,
                "withBreakfastFlag": 0,
                "breakfastSelectFlag": 0,
                "payment": "1",
                "reserveUrl": "http://img.travel.rakuten.co.jp/image/tr/api/re/IdsCY/?f_no=145279&f_syu=twn&f_hi1=2016-06-24&f_hi2=2016-06-29&f_heya_su=1&f_otona_su=1&f_s1=0&f_s2=0&f_y1=0&f_y2=0&f_y3=0&f_y4=0&f_camp_id=3296366",
                "salesformFlag": 0
              }
            },
            {
              "dailyCharge": {
                "stayDate": "2016-06-24",
                "rakutenCharge": 50000,
                "total": 50000,
                "chargeFlag": 0
              }
            }
          ]
        }
      ]
    }
  ]
}
```


### Travel/HotelRanking

#### Description

Gets the top 10 hotels by hotel genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/HotelRanking/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
genre<br>*Genre* | string | Optional | This field allows you to specify more than one in CSV format.<br>Example: <code>genre=all,onsen</code><br>If you specify the above, the API server will return the two types of rankings of overall ranking and the hot spring inn rankings.
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Travel/HotelRanking/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID&hits=3
##### Response

```json
{
  "Rankings": [
    {
      "Ranking": {
        "genre": "all",
        "title": "【楽天トラベル】お客さま評価ランキング【総合】",
        "lastBuildDate": "20141102163314",
        "hotels": [
          {
            "hotel": {
              "rank": 1,
              "hotelNo": 19756,
              "hotelName": "八ヶ岳高原　ペンション　乙女座宮",
              "middleClassName": "山梨県",
              "userReview": "八ヶ岳登山のために、友だちと利用しました。寒い雨の日でしたが、宿に着くと奥さんがとても優しく受け入れてくれ、思わずただいまと言いたいくらい安心感がありました。夜食ではお腹いっぱいなり、暖かいお風呂と清…　2014-10-22 20:57:28投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/19756/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 298,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=19756",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=19756",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=19756",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=19756",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/19756/19756.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 2,
              "hotelNo": 29176,
              "hotelName": "ペンション　プチポワ",
              "middleClassName": "福島県",
              "userReview": "予想以上でした。お風呂は温泉ではないと思いますが、補って余りあります。館内、室内とも奇麗です。食事は５点プラスアルファあげたいくらいです。奥さんの愛想のよい対応も好感が持てます。いつまでも、続けて…　2014-10-28 21:49:53投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/29176/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 224,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=29176",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=29176",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=29176",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=29176",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/29176/29176.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 3,
              "hotelNo": 20722,
              "hotelName": "コテージ・パラディーゾ",
              "middleClassName": "沖縄県",
              "userReview": "7月19日から大人３名、子ども３名で二泊させて頂きました。芝生にデッキ、景色も最高で子ども達は自由に遊び回り、親はのんびりと過ごすことができました。バーベキューも美味しく、ボリューム満点！差し入れの海…　2014-08-31 03:39:15投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/20722/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 212,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=20722",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=20722",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=20722",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=20722",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/20722/20722.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 4,
              "hotelNo": 68188,
              "hotelName": "那須温泉　ガーデンハウス　バイブリー",
              "middleClassName": "栃木県",
              "userReview": "数十年ぶりに那須を訪れました。久しぶりに宿に満足と充実感を覚える旅となりました。外観、内装、お風呂、食事、オーナーご夫妻のお人柄、隅々まで行き届いたおもてなしを感じることができました。紅葉には少し…　2014-10-12 21:03:15投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/68188/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 151,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=68188",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=68188",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=68188",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=68188",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/68188/68188.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 5,
              "hotelNo": 15599,
              "hotelName": "ホテル　デュシェルブルー",
              "middleClassName": "山梨県",
              "userReview": "１０月２４日に、山梨の実家の法事の帰りに夫と２人で一泊しました。天候に恵まれ、紅葉も始まったばかりの八ヶ岳でとてもすてきなホテルに宿泊出来ました。お部屋はもちろん庭の木１本１本にまで、オーナー夫婦の…　2014-10-26 18:11:55投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/15599/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 139,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=15599",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=15599",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=15599",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=15599",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/15599/15599.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 6,
              "hotelNo": 40476,
              "hotelName": "シェソワ　ワカミヤ",
              "middleClassName": "岐阜県",
              "userReview": "初めて利用しました。今回は、口コミを見てたので期待大てましたが、正にその通りでした。色んな意味で、満点評価です！また、利用したいと思います♪　2014-10-27 17:28:14投稿",
              "reviewCount": 124,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=40476",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=40476",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=40476",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=40476",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/40476/40476.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 7,
              "hotelNo": 74708,
              "hotelName": "民宿あしずり　岬光（はなみつ）",
              "middleClassName": "高知県",
              "userReview": "立地：足摺岬にも白山同門にも金剛福寺にもどこにでも近い好立地です。しかも部屋からは太平洋を一望できるオーシャンビュー！部屋：決して新しくなく、設備が整っているわけではありませんが、とても清潔に…　2014-08-27 09:45:45投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/74708/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 94,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=74708",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=74708",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=74708",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=74708",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/74708/74708.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 8,
              "hotelNo": 66511,
              "hotelName": "喜代美旅館",
              "middleClassName": "栃木県",
              "userReview": "８月２６日２７日と宿泊させていただきました。行き届いた、お声掛けをしていただき、大変嬉しい思いです。有難うございましたm(__)m　2014-08-28 21:17:06投稿",
              "reviewCount": 86,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=66511",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=66511",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=66511",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=66511",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/66511/66511.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 9,
              "hotelNo": 129997,
              "hotelName": "＆Ｈａｎａ　Ｓｔａｙ",
              "middleClassName": "沖縄県",
              "userReview": "豊かな自然に囲まれてゆったりと過ごすことができたことはもちろんですが、１番良かったと思うのは、２日目の鉄板焼きと２日目の朝食のパンでした。鉄板焼きのおいしさは今までの方が書かれている通りの絶品でした。…　2014-10-29 17:13:01投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/129997/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 77,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=129997",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=129997",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=129997",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=129997",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/129997/129997.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          },
          {
            "hotel": {
              "rank": 10,
              "hotelNo": 76787,
              "hotelName": "ペンションふうらいぼー",
              "middleClassName": "宮城県",
              "userReview": "１０月１２日の３連休中日に利用させていただきました。妊娠中の妻と二人だったんですが、コーヒーの代わりにカフェインレスの飲み物を出していただいたり優しい配慮があり有り難かったです☆他の方々の書き…　2014-10-15 21:12:00投稿 <a href=\"http://travel.rakuten.co.jp/HOTEL/76787/review.html\" class=\"3click\">つづきはこちら</a>",
              "reviewCount": 49,
              "hotelInformationUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/yS4PR/?f_no=76787",
              "planListUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/WrBrg/?f_flg=PLAN&f_no=76787",
              "checkAvailableUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/Ss6mg/?f_no=76787",
              "reviewUrl": "http://img.travel.rakuten.co.jp/image/tr/api/ra/vvC6h/?f_hotel_no=76787",
              "hotelImageUrl": "http://img.travel.rakuten.co.jp/share/HOTEL/76787/76787.jpg",
              "hotelThumbnailUrl": null,
              "reviewAverage": 5,
              "carrier": 0
            }
          }
        ]
      }
    }
  ]
}
```


### Travel/GetHotelChainList

#### Description

Gets the full hotel chain list.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/GetHotelChainList/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Travel/GetHotelChainList/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID
##### Response

```json
{
  "largeClasses": [
    {
      "largeClass": [
        {
          "largeClassCode": "japan",
          "hotelChains": [
            {
              "hotelChain": {
                "hotelChainCode": "AB",
                "hotelChainName": "ABホテル",
                "hotelChainNameKana": "ABホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FUWH",
                "hotelChainName": "WHG（ワシントンホテル/ホテルグレイスリー）",
                "hotelChainNameKana": "WHG（ワシントンホテル/ホテルグレイスリー）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IHGA",
                "hotelChainName": "IHG・ANA・ホテルズグループ",
                "hotelChainNameKana": "アイエイチジーエーエヌエーホテルズグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ACH",
                "hotelChainName": "アコーホテルズ",
                "hotelChainNameKana": "アコーホテルズ",
                "hotelChainComment": "アコーホテルズは全世界で約３，８００軒のホテルを展開する世界最大級のフランスのホテルチェーンです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AS",
                "hotelChainName": "アソシアホテルズ＆リゾーツ",
                "hotelChainNameKana": "アソシアホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AP",
                "hotelChainName": "アパホテルズ＆リゾーツ",
                "hotelChainNameKana": "アパホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OR",
                "hotelChainName": "アビリタス　ホスピタリティ",
                "hotelChainNameKana": "アビリタス　ホスピタリティ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AH",
                "hotelChainName": "アベストホテルズ",
                "hotelChainNameKana": "アベストホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AMMS",
                "hotelChainName": "AMMS Hotels",
                "hotelChainNameKana": "アムスホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AMBX",
                "hotelChainName": "アンビックスグループ",
                "hotelChainNameKana": "アンビックスグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AC",
                "hotelChainName": "アークホテルグループ(ルートインホテルズ)",
                "hotelChainNameKana": "アークホテルグループ(ルートインホテルズ)",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ART",
                "hotelChainName": "アートホテルズ",
                "hotelChainNameKana": "アートホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "UH",
                "hotelChainName": "アーバインホテルズ",
                "hotelChainNameKana": "アーバインホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RB",
                "hotelChainName": "Ｒ＆Ｂホテルチェーン（ワシントンホテル株式会社）",
                "hotelChainNameKana": "アールアンドビーホテルチェーン（ワシントンホテルカブシキガイシャ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IHG",
                "hotelChainName": "イシン・ホテルズ・グループ",
                "hotelChainNameKana": "イシン・ホテルズ・グループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ITO",
                "hotelChainName": "伊東園ホテルズ",
                "hotelChainNameKana": "イトウエンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BS",
                "hotelChainName": "インターコンチネンタルホテルズ（クラウンプラザ/ホリデイ・イン）",
                "hotelChainNameKana": "インターコンチネンタルホテルズ（クラウンプラザ/ホリデイ・イン）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IN",
                "hotelChainName": "インターコンチネンタルホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainNameKana": "インターコンチネンタルホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "EHO",
                "hotelChainName": "イーホテルチェーン",
                "hotelChainNameKana": "イーホテルチェーン",
                "hotelChainComment": "人と地球にやさしいホテル"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "WING",
                "hotelChainName": "ウィングインターナショナルホテルチェーン",
                "hotelChainNameKana": "ウィングインターナショナルホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "WTN",
                "hotelChainName": "ウェスティン ホテル＆リゾート(スターウッドホテル＆リゾート)",
                "hotelChainNameKana": "ウェスティン ホテルアンドリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PH",
                "hotelChainName": "HMIホテルグループ",
                "hotelChainNameKana": "エイチエムアイホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ANA",
                "hotelChainName": "ANAホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainNameKana": "エーエヌエーホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OM",
                "hotelChainName": "大江戸温泉物語",
                "hotelChainNameKana": "オオエドオンセンモノガタリ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OD",
                "hotelChainName": "小田急グループホテル",
                "hotelChainNameKana": "オダキュウグループホテル",
                "hotelChainComment": "ホテル小田急は多彩なラインナップでビジネスやレジャーにと様々なご用途にお応えします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OK",
                "hotelChainName": "オークスグループ",
                "hotelChainNameKana": "オークスグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OHJL",
                "hotelChainName": "オークラ ニッコー ホテルズ",
                "hotelChainNameKana": "オークラ ニッコー ホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OH",
                "hotelChainName": "オークラ ホテルズ＆リゾーツ(オークラ ニッコー ホテルズ)",
                "hotelChainNameKana": "オークラ ホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KAME",
                "hotelChainName": "ＨＯＴＥＬ　ＡＺ　グループ",
                "hotelChainNameKana": "カメノイホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KMR",
                "hotelChainName": "加森観光グループ",
                "hotelChainNameKana": "カモリカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KRKM",
                "hotelChainName": "カラカミ観光グループ",
                "hotelChainNameKana": "カラカミカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KARA",
                "hotelChainName": "唐津第一ホテルズ",
                "hotelChainNameKana": "カラツダイイチホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CA",
                "hotelChainName": "ＣＡＮＤＥＯ　ＨＯＴＥＬＳ(カンデオホテルズ)",
                "hotelChainNameKana": "カンデオホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KAMP",
                "hotelChainName": "かんぽの宿",
                "hotelChainNameKana": "カンポノヤド",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GP",
                "hotelChainName": "ガーデンパレスチェーン",
                "hotelChainNameKana": "ガーデンパレスチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "QK",
                "hotelChainName": "休暇村",
                "hotelChainNameKana": "キュウカムラ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KYGR",
                "hotelChainName": "休暇村グループの宿",
                "hotelChainNameKana": "キュウカムラグループノヤド",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KT",
                "hotelChainName": "京都タワーホテルチェーン",
                "hotelChainNameKana": "キョウトタワーホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KMHS",
                "hotelChainName": "共立メンテナンス　HOTEL＆SPA",
                "hotelChainNameKana": "キョウリツメンテナンス　ホテルアンドスパ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KRTK",
                "hotelChainName": "くれたけホテルチェーン",
                "hotelChainNameKana": "クレタケホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GI",
                "hotelChainName": "グッドイングループ",
                "hotelChainNameKana": "グッドイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GH",
                "hotelChainName": "グランパークホテルグループ",
                "hotelChainNameKana": "グランパークホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GVH",
                "hotelChainName": "グランビスタ　ホテル＆リゾート",
                "hotelChainNameKana": "グランビスタ　ホテル＆リゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GV",
                "hotelChainName": "グランヴィリオホテル(ルートインホテルズ)",
                "hotelChainNameKana": "グランヴィリオホテル(ルートインホテルズ)",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GG",
                "hotelChainName": "グリーンズホテルズ",
                "hotelChainNameKana": "グリーンズホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GHM",
                "hotelChainName": "グリーンホスピタリティーマネジメント",
                "hotelChainNameKana": "グリーンホスピタリティーマネジメント",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GHC",
                "hotelChainName": "グリーンリッチホテルズ",
                "hotelChainNameKana": "グリーンリッチホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KP",
                "hotelChainName": "京王プラザホテルチェーン",
                "hotelChainNameKana": "ケイオウプラザホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KEIO",
                "hotelChainName": "京王プレッソインチェーン",
                "hotelChainNameKana": "ケイオウプレッソインチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KKEX",
                "hotelChainName": "京急イーエックスイングループ",
                "hotelChainNameKana": "ケイキュウイーエックスイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KKR",
                "hotelChainName": "ＫＫＲホテルズ＆リゾーツ",
                "hotelChainNameKana": "ケーケーアールホテルズアンドリゾーツ",
                "hotelChainComment": "全国の観光地や主要都市に点在するKKRネットワークで観光にビジネスに皆様のお越しをお待ちしております"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KRT",
                "hotelChainName": "公立学校共済組合",
                "hotelChainNameKana": "コウリツガッコウキョウサイクミアイ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KH",
                "hotelChainName": "国際興業グループホテル",
                "hotelChainNameKana": "コクサイコウギョウグループホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KO",
                "hotelChainName": "国際ホテルグループ",
                "hotelChainNameKana": "コクサイホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CHJG",
                "hotelChainName": "コンフォートホテル",
                "hotelChainNameKana": "コンフォートホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MC",
                "hotelChainName": "コート・ホテルズ・アンド・リゾーツ",
                "hotelChainNameKana": "コート・ホテルズ・アンド・リゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SF",
                "hotelChainName": "サフィールホテルズ",
                "hotelChainNameKana": "サフィールホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SAKO",
                "hotelChainName": "三交イングループ",
                "hotelChainNameKana": "サンコウイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SH",
                "hotelChainName": "サンルートホテルチェーン",
                "hotelChainNameKana": "サンルートホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SR",
                "hotelChainName": "サンルートホテルチェーン（サンネット）",
                "hotelChainNameKana": "サンルートホテルチェーン（サンネット）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "STRW",
                "hotelChainName": "シェラトン ホテル&リゾート(スターウッドホテル＆リゾート)",
                "hotelChainNameKana": "シェラトン ホテルアンドリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SLPH",
                "hotelChainName": "シーラックパルホテルズ",
                "hotelChainNameKana": "シーラックパルホテルズ",
                "hotelChainComment": "ホテルシーラックパルは「お値段三流設備は一流」をモットーに、お客様へより快適な空間をご提供致します。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JRQ",
                "hotelChainName": "ＪＲ九州ホテルグループ",
                "hotelChainNameKana": "ジェイアールキュウシュウホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JRWN",
                "hotelChainName": "ＪＲ西日本ウェルネット（弥生会館）",
                "hotelChainNameKana": "ジェイアールニシニホンウェルネット（ヤヨイカイカン）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JW",
                "hotelChainName": "ＪＲ西日本ホテルズ",
                "hotelChainNameKana": "ジェイアールニシニホンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JRWV",
                "hotelChainName": "ジェイアール西日本ヴィアインホテルグループ",
                "hotelChainNameKana": "ジェイアールニシニホンヴィアインホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JK",
                "hotelChainName": "ＪＲ北海道グループ",
                "hotelChainNameKana": "ジェイアールホッカイドウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JASM",
                "hotelChainName": "ジャスマックグループ",
                "hotelChainNameKana": "ジャスマックグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JAL",
                "hotelChainName": "JALホテル(オークラ ニッコー ホテルズ)",
                "hotelChainNameKana": "ジャルホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JU",
                "hotelChainName": "聚楽（じゅらく）チェーン",
                "hotelChainNameKana": "ジュラク（ジュラク）チェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SKY",
                "hotelChainName": "スカイコートグループ",
                "hotelChainNameKana": "スカイコートグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SW",
                "hotelChainName": "スターウッドホテル＆リゾート",
                "hotelChainNameKana": "スターウッドホテル＆リゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "STAR",
                "hotelChainName": "スターツグループ",
                "hotelChainNameKana": "スターツグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ST",
                "hotelChainName": "スターホテルグループ",
                "hotelChainNameKana": "スターホテルグループ",
                "hotelChainComment": "旅の一等地と主要都市のベストポイント。スターホテルグループは皆さまをおもてなしいたします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SML",
                "hotelChainName": "スマイルホテル・プレミアイン",
                "hotelChainNameKana": "スマイルホテル・プレミアイン",
                "hotelChainComment": "全国に広がるスマイルホテル！ビジネスに観光に、明るい笑顔で皆様をサポートします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "VIRF",
                "hotelChainName": "住友不動産ヴィラフォンテーヌ",
                "hotelChainNameKana": "スミトモフドウサンヴィラフォンテーヌグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SPH",
                "hotelChainName": "スーパーホテル",
                "hotelChainNameKana": "スーパーホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IZ",
                "hotelChainName": "セラヴィリゾート泉郷",
                "hotelChainNameKana": "セラヴィリゾートイズミゴウ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SI",
                "hotelChainName": "セレクト ホテルズ",
                "hotelChainNameKana": "セレクト ホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CH",
                "hotelChainName": "セントラルホテルチェーン",
                "hotelChainNameKana": "セントラルホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ZK",
                "hotelChainName": "全九州第一ホテルチェーン",
                "hotelChainNameKana": "ゼンキュウシュウダイイチホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ZN",
                "hotelChainName": "全日空ホテルズ（IHG・ANA・ホテルズグループ）",
                "hotelChainNameKana": "ゼンニックウホテルズ（アイエイチジーエーエヌエーホテルズグループ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "STF",
                "hotelChainName": "相鉄イングループ",
                "hotelChainNameKana": "ソウテツイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CSO",
                "hotelChainName": "ソラーレコレクション（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainNameKana": "ソラーレコレクション（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DH",
                "hotelChainName": "第一寶亭留グループ",
                "hotelChainNameKana": "ダイイチホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DRNT",
                "hotelChainName": "ダイワロイネットホテルズ",
                "hotelChainNameKana": "ダイワロイネットホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DW",
                "hotelChainName": "ダイワロイヤルホテルズ",
                "hotelChainNameKana": "ダイワロイヤルホテルズ",
                "hotelChainComment": "広い客室、充実した設備・アメニティ。ワンランク上質な“やさしさ”で、お客様をお待ちしております。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CS",
                "hotelChainName": "チサンホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainNameKana": "チサンホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TG",
                "hotelChainName": "鶴雅グループ",
                "hotelChainNameKana": "ツルガグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TE",
                "hotelChainName": "東映ホテルチェーン",
                "hotelChainNameKana": "トウエイホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TST",
                "hotelChainName": "東急ステイ",
                "hotelChainNameKana": "トウキュウステイ",
                "hotelChainComment": "広さと安心を備えた新しいスタイルの滞在空間には、充実の設備を取り揃えております。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TI",
                "hotelChainName": "東急ホテルズ",
                "hotelChainNameKana": "トウキュウホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKE",
                "hotelChainName": "東急ホテルズ（エクセルホテル東急）",
                "hotelChainNameKana": "トウキュウホテルズ（エクセルホテルトウキュウ）",
                "hotelChainComment": "洗練された現代的スタイルのスーペリアホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKI",
                "hotelChainName": "東急ホテルズ（東急REIホテル）",
                "hotelChainNameKana": "トウキュウホテルズ（トウキュウREIホテルズ）",
                "hotelChainComment": "ビジネスステイをサポートする機能的な空間のスタンダードホテル。テンピュール枕を全室に設置。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKR",
                "hotelChainName": "東急ホテルズ（パートナーズホテル）",
                "hotelChainNameKana": "トウキュウホテルズ（パートナーズホテル）",
                "hotelChainComment": "自然と調和し、日常を離れたハイグレードなくつろぎに満たされるリゾートホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKH",
                "hotelChainName": "東急ホテル（東急ホテルズ）",
                "hotelChainNameKana": "トウキュウホテル（トウキュウホテルズ）",
                "hotelChainComment": "信頼と品格のあるおもてなしのラグジュアリーホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TLND",
                "hotelChainName": "東急リゾートサービス",
                "hotelChainNameKana": "トウキュウリゾートサービス",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TB",
                "hotelChainName": "東武ホテルチェーン",
                "hotelChainNameKana": "トウブホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TY",
                "hotelChainName": "東横イン",
                "hotelChainNameKana": "トウヨコイン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DU",
                "hotelChainName": "ドーミーイン",
                "hotelChainNameKana": "ドーミーイン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NI",
                "hotelChainName": "ナインアワーズ",
                "hotelChainNameKana": "ナインアワーズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NAQ",
                "hotelChainName": "ナクア ホテル＆リゾーツ",
                "hotelChainNameKana": "ナクア ホテル＆リゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "YM",
                "hotelChainName": "南西楽園リゾート",
                "hotelChainNameKana": "ナンセイラクエンリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NNR",
                "hotelChainName": "西鉄ホテルグループ",
                "hotelChainNameKana": "ニシテツホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NK",
                "hotelChainName": "ニッコー・ホテルズ・インターナショナル(オークラ ニッコー ホテルズ）",
                "hotelChainNameKana": "ニッコー・ホテルズ・インターナショナル",
                "hotelChainComment": "快適という名の時間。優雅なひとときをご提供するニッコー・ホテルズ・インターナショナル"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NO",
                "hotelChainName": "ニューオリエンタルホテルグループ",
                "hotelChainNameKana": "ニューオリエンタルホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NT",
                "hotelChainName": "ニューオータニホテルズ",
                "hotelChainNameKana": "ニューオータニホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NGH",
                "hotelChainName": "ニューグロリアホテルグループ",
                "hotelChainNameKana": "ニューグロリアホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NES",
                "hotelChainName": "ネストホテルグループ",
                "hotelChainNameKana": "ネストホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NGCK",
                "hotelChainName": "野口観光グループ",
                "hotelChainNameKana": "ノグチカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HY",
                "hotelChainName": "ハイアットホテルズアンドリゾーツ",
                "hotelChainNameKana": "ハイアットホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HPR",
                "hotelChainName": "ハイパーホテルズ",
                "hotelChainNameKana": "ハイパーホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HK",
                "hotelChainName": "阪急阪神第一ホテルグループ　　",
                "hotelChainNameKana": "ハンキュウハンシンダイイチホテルグループ　　",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HTN",
                "hotelChainName": "ハートンホテルチェーン",
                "hotelChainNameKana": "ハートンホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PA",
                "hotelChainName": "パレスホテルチェーン",
                "hotelChainNameKana": "パレスホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PL",
                "hotelChainName": "パールホテルグループ",
                "hotelChainNameKana": "パールホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HI",
                "hotelChainName": "ヒルトングループ",
                "hotelChainNameKana": "ヒルトングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "VHG",
                "hotelChainName": "ビスタホテルグループ",
                "hotelChainNameKana": "ビスタホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BIG",
                "hotelChainName": "BigWeek",
                "hotelChainNameKana": "ビッグウィーク",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "VW",
                "hotelChainName": "ビューホテルズ",
                "hotelChainNameKana": "ビューホテルズ",
                "hotelChainComment": "全国に広がるビューホテルズは只今１６！真心のこもったおもてなしで快適なホテルライフをお約束致します。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MI",
                "hotelChainName": "ファミリーオ・フォルクローロ（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "ファミリーオ・フォルクローロ(ジェイアールヒガシニホンホテルズ)",
                "hotelChainComment": "ファミリーにも利用しやすい手頃な価格と親しみやすいサービスの長期滞在型ホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HATA",
                "hotelChainName": "ファミリーロッジ旅籠屋",
                "hotelChainNameKana": "ファミリーロッジハタゴヤ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FC",
                "hotelChainName": "ファーストキャビン",
                "hotelChainNameKana": "ファーストキャビン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FURI",
                "hotelChainName": "藤田観光グループ",
                "hotelChainNameKana": "フジタカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BRH",
                "hotelChainName": "ブライトンホテルズ",
                "hotelChainNameKana": "ブライトンホテルズ",
                "hotelChainComment": "総支配人の目が行き届く、パーソナルサービスの提供。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BW",
                "hotelChainName": "ブルーウェーブインホテルチェーン",
                "hotelChainNameKana": "ブルーウェーブインホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PRH",
                "hotelChainName": "プリンスホテル",
                "hotelChainNameKana": "プリンスホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KEN",
                "hotelChainName": "プレミアホテルグループ",
                "hotelChainNameKana": "プレミアホテルグループ",
                "hotelChainComment": "上質かつ快適なご滞在を叶えるプレミアホテルグループ。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BWH",
                "hotelChainName": "ベストウェスタンホテルズ",
                "hotelChainNameKana": "ベストウェスタンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SLP",
                "hotelChainName": "ベッセルホテルズ",
                "hotelChainNameKana": "ベッセルホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BHG",
                "hotelChainName": "ベネフィットホテル　グループ",
                "hotelChainNameKana": "ベネフィットホテル　グループ",
                "hotelChainComment": "お客様がどんな目的で何を求めておられるのか…その願いが叶うお手伝いをします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HR",
                "hotelChainName": "星野リゾートグループ",
                "hotelChainNameKana": "ホシノリゾートグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "A1",
                "hotelChainName": "ホテルアルファ−ワンチェーン",
                "hotelChainNameKana": "ホテルアルファ−ワンチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GRP",
                "hotelChainName": "ホテルグリーンプラザチェーン",
                "hotelChainNameKana": "ホテルグリーンプラザチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KEI",
                "hotelChainName": "ホテル京阪チェーン",
                "hotelChainNameKana": "ホテルケイハンチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JL",
                "hotelChainName": "ホテルＪＡＬシティ(オークラ ニッコー ホテルズ）",
                "hotelChainNameKana": "ホテルジャルシティ",
                "hotelChainComment": "明日へと繋がる空間。シティホテルの手軽さと質の高い快適なひとときをお約束するホテルJALシティ"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKB",
                "hotelChainName": "ホテル東急ビズフォート（東急ホテルズ）",
                "hotelChainNameKana": "ホテルトウキュウビズフォート（トウキュウホテルズ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TRST",
                "hotelChainName": "ホテルトラスティグループ",
                "hotelChainNameKana": "ホテルトラスティグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PIN",
                "hotelChainName": "ホテルパインヒルグループ",
                "hotelChainNameKana": "ホテルパインヒルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HEJ",
                "hotelChainName": "ホテル東日本グループ",
                "hotelChainNameKana": "ホテルヒガシニホングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HC",
                "hotelChainName": "ホテル法華クラブグループ",
                "hotelChainNameKana": "ホテルホッケクラブグループ",
                "hotelChainComment": "全国１６店舗を展開するオンリーワンなホスピタリティーホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MT",
                "hotelChainName": "ホテルメッツ（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "ホテルメッツ（ジェイアールヒガシニホンホテルズ）",
                "hotelChainComment": "リーズナブルな料金、しかもシティホテル並のグレード感あふれる客室、新ビジネスクラスのホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MO",
                "hotelChainName": "ホテルモントレグループ",
                "hotelChainNameKana": "ホテルモントレグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "H3",
                "hotelChainName": "ホテルリソルチェーン",
                "hotelChainNameKana": "ホテルリソルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "H123",
                "hotelChainName": "ホテル１ー２ー３グループ",
                "hotelChainNameKana": "ホテルワンツースリーグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "WM",
                "hotelChainName": "マイステイズホテルチェーン",
                "hotelChainNameKana": "マイステイズホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MA",
                "hotelChainName": "マリオットグループ",
                "hotelChainNameKana": "マリオットグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MD",
                "hotelChainName": "マロウドチェーン",
                "hotelChainNameKana": "マロウドチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BASE",
                "hotelChainName": "万世閣ホテルズ",
                "hotelChainNameKana": "マンセイカクホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MNTN",
                "hotelChainName": "マンテンホテルグループ",
                "hotelChainNameKana": "マンテンホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MS",
                "hotelChainName": "マークスホテルズ",
                "hotelChainNameKana": "マークスホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GR",
                "hotelChainName": "三井ガーデンホテルズ",
                "hotelChainNameKana": "ミツイガーデンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KI",
                "hotelChainName": "都ホテルズ＆リゾーツ",
                "hotelChainNameKana": "ミヤコホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ME",
                "hotelChainName": "名鉄ホテル旅館グループ",
                "hotelChainNameKana": "メイテツホテルリョカングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MH",
                "hotelChainName": "メトロポリタンホテルズ（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "メトロポリタンホテルズ（ジェイアールヒガシニホンホテルズ）",
                "hotelChainComment": "駅に近く、ビジネスや観光の拠点にフットワーク抜群のシティホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MRC",
                "hotelChainName": "メルコリゾートサービス",
                "hotelChainNameKana": "メルコリゾートサービス",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MEL",
                "hotelChainName": "メルパルクチェーン",
                "hotelChainNameKana": "メルパルクチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MB",
                "hotelChainName": "森トラスト・ホテルズ&リゾーツ",
                "hotelChainNameKana": "モリトラスト・ホテルズ&リゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "YK",
                "hotelChainName": "弥生会館（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "ヤヨイカイカン(ジェイアールヒガシニホンホテルズ）",
                "hotelChainComment": "浜離宮の緑に囲まれ、都心にいながら自然のやすらぎに恵まれたホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "YR",
                "hotelChainName": "湯快リゾート",
                "hotelChainNameKana": "ユカイリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "UNI",
                "hotelChainName": "ユニゾホテルグループ",
                "hotelChainNameKana": "ユニゾホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "UV",
                "hotelChainName": "ユニバーサルホテルチェーン",
                "hotelChainNameKana": "ユニバーサルホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RT",
                "hotelChainName": "リステルホテルズ",
                "hotelChainNameKana": "リステルホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RI",
                "hotelChainName": "リッチホテルチェーン",
                "hotelChainNameKana": "リッチホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RNET",
                "hotelChainName": "リッチモンドホテルズ",
                "hotelChainNameKana": "リッチモンドホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "LM",
                "hotelChainName": "リブマックスホテルズ",
                "hotelChainNameKana": "リブマックスホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RR",
                "hotelChainName": "リーガロイヤルホテルグループ",
                "hotelChainNameKana": "リーガロイヤルホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RE",
                "hotelChainName": "ルネッサンスホテルグループ",
                "hotelChainNameKana": "ルネッサンスホテルグループ",
                "hotelChainComment": "『駅近くリーズナブルな料金のデザイナーズホテル。広々としたバスルームが人気。』"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RU",
                "hotelChainName": "ルートイン",
                "hotelChainNameKana": "ルートイン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RP",
                "hotelChainName": "レオパレスホテルズ",
                "hotelChainNameKana": "レオパレスホテルズ",
                "hotelChainComment": "すべてのお部屋で、オンデマンドビデオ４本・ＬＡＮ接続・ＣＳ放送が無料でご利用いただけます。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ROPI",
                "hotelChainName": "ロイヤルパインズホテルズ",
                "hotelChainNameKana": "ロイヤルパインズホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RO",
                "hotelChainName": "ロイヤルパークホテルズ",
                "hotelChainNameKana": "ロイヤルパークホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "LSH",
                "hotelChainName": "ロワジールホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainNameKana": "ロワジールホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FWHP",
                "hotelChainName": "ワシントンホテルプラザ（ワシントンホテル株式会社）",
                "hotelChainNameKana": "ワシントンホテルプラザ（ワシントンホテルカブシキガイシャ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KOS",
                "hotelChainName": "ＫＯＳＣＯＩＮＮグループ",
                "hotelChainNameKana": "ＫＯＳＣＯＩＮＮグループ",
                "hotelChainComment": ""
              }
            }
          ]
        }
      ]
    }
  ]
}
```


### Travel/GetAreaClass

#### Description

Gets the full area class list.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/GetAreaClass/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Travel/GetAreaClass/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID
##### Response

```json
{
  "areaClasses": {
    "largeClasses": [
      {
        "largeClass": [
          {
            "largeClassCode": "japan",
            "largeClassName": "日本"
          },
          {
            "middleClasses": [
              {
                "middleClass": [
                  {
                    "middleClassCode": "hokkaido",
                    "middleClassName": "北海道"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sapporo",
                            "smallClassName": "札幌市内"
                          },
                          {
                            "detailClasses": [
                              {
                                "detailClass": {
                                  "detailClassCode": "A",
                                  "detailClassName": "JR札幌駅周辺・新札幌駅"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "B",
                                  "detailClassName": "大通公園周辺（テレビ塔・時計台・狸小路）"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "C",
                                  "detailClassName": "すすきの・中島公園周辺"
                                }
                              }
                            ]
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "jozankei",
                            "smallClassName": "定山渓"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "wakkanai",
                            "smallClassName": "稚内・利尻・礼文・豊富・苫前・留萌"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "abashiri",
                            "smallClassName": "網走・紋別・北見・知床"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kushiro",
                            "smallClassName": "釧路・阿寒・川湯・根室"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "obihiro",
                            "smallClassName": "帯広・十勝"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hidaka",
                            "smallClassName": "日高・えりも"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "furano",
                            "smallClassName": "富良野・美瑛・トマム"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "asahikawa",
                            "smallClassName": "旭川・層雲峡・滝川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chitose",
                            "smallClassName": "千歳・支笏・苫小牧・夕張"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "otaru",
                            "smallClassName": "小樽・余市・積丹・キロロ"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "niseko",
                            "smallClassName": "ルスツ・ニセコ・倶知安"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hakodate",
                            "smallClassName": "函館・湯の川・大沼・奥尻"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "noboribetsu",
                            "smallClassName": "登別・洞爺・室蘭"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "aomori",
                    "middleClassName": "青森県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "aomori",
                            "smallClassName": "青森市内・浅虫温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsugaru",
                            "smallClassName": "津軽半島・五所川原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ntsugaru",
                            "smallClassName": "西津軽地区"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hirosaki",
                            "smallClassName": "弘前・黒石"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "towadako",
                            "smallClassName": "八甲田・奥入瀬・十和田湖周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hachinohe",
                            "smallClassName": "八戸・三沢・古牧"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shimokita",
                            "smallClassName": "下北半島（むつ・大間）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "iwate",
                    "middleClassName": "岩手県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "morioka",
                            "smallClassName": "盛岡市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shizukuishi",
                            "smallClassName": "雫石"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "appi",
                            "smallClassName": "安比高原・八幡平・二戸"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kuji",
                            "smallClassName": "陸中海岸北部（久慈・宮古・岩泉）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ofunato",
                            "smallClassName": "陸中海岸南部（大船渡・陸前高田・釜石）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kitakami",
                            "smallClassName": "北上・花巻・遠野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ichinoseki",
                            "smallClassName": "奥州・平泉・一関"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "miyagi",
                    "middleClassName": "宮城県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sendai",
                            "smallClassName": "仙台市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "akiu",
                            "smallClassName": "秋保・作並"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "naruko",
                            "smallClassName": "鳴子・古川・くりこま高原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "matsushima",
                            "smallClassName": "松島・塩釜・石巻・南三陸・気仙沼"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shiroishi",
                            "smallClassName": "白石・宮城蔵王"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "akita",
                    "middleClassName": "秋田県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "akita",
                            "smallClassName": "秋田市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "noshiro",
                            "smallClassName": "能代・男鹿・白神"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "odate",
                            "smallClassName": "大館・鹿角・八幡平"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tazawa",
                            "smallClassName": "田沢湖・角館・大曲"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "omagari",
                            "smallClassName": "湯沢・横手"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "honjo",
                            "smallClassName": "由利本荘・鳥海山"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "yamagata",
                    "middleClassName": "山形県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yamagata",
                            "smallClassName": "山形市内・蔵王・かみのやま温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yonezawa",
                            "smallClassName": "米沢・長井・赤湯・高畠"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "murayama",
                            "smallClassName": "村山・天童"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "mogami",
                            "smallClassName": "新庄・最上・尾花沢"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shonai",
                            "smallClassName": "酒田・鶴岡・湯野浜・温海"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "hukushima",
                    "middleClassName": "福島県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fukushima",
                            "smallClassName": "福島市内・二本松"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "aizu",
                            "smallClassName": "会津若松・喜多方"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "bandai",
                            "smallClassName": "猪苗代・表磐梯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "urabandai",
                            "smallClassName": "磐梯高原・裏磐梯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "koriyama",
                            "smallClassName": "郡山・磐梯熱海"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "minami",
                            "smallClassName": "南会津（下郷・只見・檜枝岐村）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nakadori",
                            "smallClassName": "須賀川・白河"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hamadori",
                            "smallClassName": "浜通り（いわき・南相馬・相馬）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "ibaragi",
                    "middleClassName": "茨城県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "mito",
                            "smallClassName": "水戸・笠間"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "oarai",
                            "smallClassName": "大洗・ひたちなか"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hitachi",
                            "smallClassName": "日立・北茨城・奥久慈"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsukuba",
                            "smallClassName": "つくば・土浦・取手"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yuki",
                            "smallClassName": "結城・筑西・古河"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsuchiura",
                            "smallClassName": "鹿嶋・潮来・北浦"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "tochigi",
                    "middleClassName": "栃木県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "utsunomiya",
                            "smallClassName": "宇都宮・さくら"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nikko",
                            "smallClassName": "日光・中禅寺湖・今市"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kinugawa",
                            "smallClassName": "鬼怒川・川治・湯西川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nasu",
                            "smallClassName": "那須・板室・黒磯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shiobara",
                            "smallClassName": "塩原・矢板・大田原・西那須野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "mashiko",
                            "smallClassName": "益子･真岡・茂木"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "koyama",
                            "smallClassName": "小山・足利・栃木・佐野"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "gunma",
                    "middleClassName": "群馬県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "maebashi",
                            "smallClassName": "前橋市内（赤城高原含む）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ikaho",
                            "smallClassName": "伊香保温泉・渋川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "manza",
                            "smallClassName": "万座･嬬恋･北軽井沢"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kusatsu",
                            "smallClassName": "草津・白根"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shimaonsen",
                            "smallClassName": "四万温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "numata",
                            "smallClassName": "水上・猿ヶ京・沼田"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "oze",
                            "smallClassName": "尾瀬・丸沼"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kiryu",
                            "smallClassName": "桐生・伊勢崎・太田・館林"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "takasaki",
                            "smallClassName": "高崎市街"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fujioka",
                            "smallClassName": "藤岡・妙義・安中・磯部温泉"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "saitama",
                    "middleClassName": "埼玉県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "saitama",
                            "smallClassName": "さいたま（大宮・浦和）・川口・上尾"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kasukabe",
                            "smallClassName": "草加・春日部・羽生"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kumagaya",
                            "smallClassName": "熊谷・深谷・本庄"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kawagoe",
                            "smallClassName": "川越・和光・東松山・志木"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tokorozawa",
                            "smallClassName": "所沢・狭山・飯能"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chichibu",
                            "smallClassName": "秩父・長瀞"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "tiba",
                    "middleClassName": "千葉県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chiba",
                            "smallClassName": "千葉市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "keiyo",
                            "smallClassName": "舞浜・船橋・幕張"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kashiwa",
                            "smallClassName": "松戸・柏・佐倉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "narita",
                            "smallClassName": "成田空港周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "choshi",
                            "smallClassName": "銚子・佐原・東金・九十九里"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sotobo",
                            "smallClassName": "外房（鴨川・勝浦・御宿・茂原・養老渓谷）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tateyama",
                            "smallClassName": "南房総（館山・白浜･千倉）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "uchibo",
                            "smallClassName": "内房（市原・木更津・君津・富津）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "tokyo",
                    "middleClassName": "東京都"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tokyo",
                            "smallClassName": "東京２３区内"
                          },
                          {
                            "detailClasses": [
                              {
                                "detailClass": {
                                  "detailClassCode": "A",
                                  "detailClassName": "東京駅・銀座・日本橋・秋葉原"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "B",
                                  "detailClassName": "新橋・汐留・お台場"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "C",
                                  "detailClassName": "赤坂・六本木・麻布・永田町"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "D",
                                  "detailClassName": "渋谷・青山・恵比寿・目黒"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "E",
                                  "detailClassName": "品川・蒲田・羽田空港"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "F",
                                  "detailClassName": "新宿・中野・杉並"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "G",
                                  "detailClassName": "池袋・赤羽・板橋・練馬"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "H",
                                  "detailClassName": "御茶ノ水・水道橋・飯田橋"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "I",
                                  "detailClassName": "上野・浅草・両国・足立"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "J",
                                  "detailClassName": "江東・江戸川・新小岩"
                                }
                              }
                            ]
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nishi",
                            "smallClassName": "東京西部（立川・八王子・町田・府中・吉祥寺）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "okutama",
                            "smallClassName": "奥多摩・青梅・羽村"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ritou",
                            "smallClassName": "八丈島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "oshima",
                            "smallClassName": "大島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kouzu",
                            "smallClassName": "神津島・新島・式根島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "miyake",
                            "smallClassName": "三宅島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "Ogasawara",
                            "smallClassName": "小笠原諸島"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "kanagawa",
                    "middleClassName": "神奈川県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yokohama",
                            "smallClassName": "横浜市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kawasaki",
                            "smallClassName": "川崎市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hakone",
                            "smallClassName": "箱根"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "odawara",
                            "smallClassName": "小田原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yugawara",
                            "smallClassName": "湯河原・真鶴"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sagamiko",
                            "smallClassName": "相模湖・丹沢"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sagamihara",
                            "smallClassName": "相模原･大和"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ebina",
                            "smallClassName": "海老名・厚木・伊勢原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shonan",
                            "smallClassName": "湘南（鎌倉・藤沢・茅ヶ崎・平塚・江ノ島・大磯）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "miura",
                            "smallClassName": "三浦半島（横須賀・三浦）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "niigata",
                    "middleClassName": "新潟県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "niigata",
                            "smallClassName": "新潟市"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kaetsu",
                            "smallClassName": "新発田（月岡）・村上（瀬波）・咲花"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kita",
                            "smallClassName": "長岡・燕・三条・寺泊"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "minami",
                            "smallClassName": "魚沼・十日町・津南・六日町・大湯温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yuzawa",
                            "smallClassName": "湯沢･苗場"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "joetsu",
                            "smallClassName": "柏崎・上越・妙高・糸魚川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sado",
                            "smallClassName": "佐渡"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "toyama",
                    "middleClassName": "富山県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "toyama",
                            "smallClassName": "富山市･八尾･立山山麓"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "goto",
                            "smallClassName": "滑川・魚津・黒部・宇奈月"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gosei",
                            "smallClassName": "高岡・砺波・新湊・氷見・小矢部・射水"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "ishikawa",
                    "middleClassName": "石川県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kanazawa",
                            "smallClassName": "金沢市内・周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kaga",
                            "smallClassName": "加賀（山代・山中・片山津）・小松（粟津）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "noto",
                            "smallClassName": "能登・輪島・珠洲"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nanao",
                            "smallClassName": "七尾・和倉・羽咋"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "hukui",
                    "middleClassName": "福井県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hukui",
                            "smallClassName": "福井市"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "awara",
                            "smallClassName": "あわら・三国"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "katsuyama",
                            "smallClassName": "永平寺・勝山・大野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "echizen",
                            "smallClassName": "越前・鯖江・武生"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsuruga",
                            "smallClassName": "敦賀・美浜"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "obama",
                            "smallClassName": "若狭・小浜・高浜"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "yamanasi",
                    "middleClassName": "山梨県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kofu",
                            "smallClassName": "甲府市内・昇仙峡・甲斐"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yamanashi",
                            "smallClassName": "山梨・石和・勝沼・塩山"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "otsuki",
                            "smallClassName": "大月・都留"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fujisan",
                            "smallClassName": "富士吉田・忍野・山中湖・富士山"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kawaguchiko",
                            "smallClassName": "河口湖・西湖・精進湖・本栖湖"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "minobu",
                            "smallClassName": "身延・下部温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nirasaki",
                            "smallClassName": "韮崎・南アルプス"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kiyosato",
                            "smallClassName": "八ヶ岳・小淵沢・清里・大泉"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "nagano",
                    "middleClassName": "長野県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nagano",
                            "smallClassName": "長野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "madara",
                            "smallClassName": "斑尾・黒姫・飯綱･戸隠"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nozawa",
                            "smallClassName": "野沢温泉・木島平・戸狩"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shiga",
                            "smallClassName": "志賀高原･湯田中･渋"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ueda",
                            "smallClassName": "上田・別所・鹿教湯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chikuma",
                            "smallClassName": "戸倉上山田・千曲"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sugadaira",
                            "smallClassName": "菅平・峰の原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "karui",
                            "smallClassName": "軽井沢・佐久･小諸"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yatsu",
                            "smallClassName": "八ヶ岳（野辺山･富士見高原･原村）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kirigamine",
                            "smallClassName": "白樺湖・車山・蓼科・霧ヶ峰"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "suwa",
                            "smallClassName": "諏訪湖周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ina",
                            "smallClassName": "伊那・飯田・駒ヶ根・昼神"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kiso",
                            "smallClassName": "木曽"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "matsumo",
                            "smallClassName": "松本・浅間温泉・塩尻"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kamiko",
                            "smallClassName": "上高地・白骨・乗鞍"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hotaka",
                            "smallClassName": "豊科・穂高・安曇野・大町"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hakuba",
                            "smallClassName": "白馬・小谷"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "gihu",
                    "middleClassName": "岐阜県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gifu",
                            "smallClassName": "岐阜・各務原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kamitakara",
                            "smallClassName": "奥飛騨・新穂高"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "takayama",
                            "smallClassName": "高山・飛騨"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gero",
                            "smallClassName": "下呂温泉・濁河温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tajimi",
                            "smallClassName": "多治見・恵那・中津川・美濃加茂・可児"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gujo",
                            "smallClassName": "郡上八幡・関・美濃"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shirakawago",
                            "smallClassName": "白川郷"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ogaki",
                            "smallClassName": "大垣・岐阜羽島"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "shizuoka",
                    "middleClassName": "静岡県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shizuoka",
                            "smallClassName": "静岡市（静岡・清水）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "atami",
                            "smallClassName": "熱海"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ito",
                            "smallClassName": "伊東"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "izukogen",
                            "smallClassName": "伊豆高原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "higashi",
                            "smallClassName": "東伊豆・河津"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shimoda",
                            "smallClassName": "下田・南伊豆"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nishi",
                            "smallClassName": "西伊豆（戸田・土肥･堂ヶ島・松崎）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "naka",
                            "smallClassName": "中伊豆（伊豆長岡・修善寺・天城湯ヶ島）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fuji",
                            "smallClassName": "富士・富士宮"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "numazu",
                            "smallClassName": "三島・沼津・御殿場"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yaizu",
                            "smallClassName": "焼津・藤枝・御前崎・寸又峡"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hamamatsu",
                            "smallClassName": "浜松・浜名湖・天竜"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kikugawa",
                            "
```


### Travel/KeywordHotelSearch

#### Description

Gets up to 30 hotels by keyword.
#### Resource URL

https://app.rakuten.co.jp/services/api/Travel/KeywordHotelSearch/20131024
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
page<br>*Result page* | integer | Optional | Number of page.<br>Integer between 1 and 100.
hits<br>*How many results per page* | integer | Optional | Parameters that determines the number of results per page.<br>Integer from 1 to 30.
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.
keyword<br>*Search Keyword* | string | Required | When you specify more than one keyword separated by an space character it is considered an AND search.<br>Your search must contain at least 2 characters.
middleClassCode<br>*Middle class code* | string | Optional | Code specifying the prefecture.<br>Please get this value from the GetAreaClass API.
searchField<br>*Search scope* | integer | Optional | Specify the target scope of the keyword search.
hotelChainCode<br>*Hotel chain code* | string | Optional | Code for specifying the hotel chain.<br>If this field is specified, only hotels belonging to the specified hotel chain will be searched.<br>Please get the hotel chain list from the GetHotelChainList API.<br>This field allows you to specify up to 5 hotel chains separated by commas.<br>Example: <code>hotelChainCode=JL,NK</code>
hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.
responseType<br>*Response Type* | string | Optional | Specify the amount of information returned in the response:
sort<br>*Sort* | string | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>


## Rakuten Auction

![Rakuten Auction](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-auctions.png)
* **Name** Rakuten Auction
* **URL** http://auction.rakuten.co.jp/
* **Description** Rakuten's auction website.

### AuctionGenreId/Search

#### Description

Gets an auction genre's attributes, children genres and ancestor genres by auction genre id.
#### Resource URL

https://app.rakuten.co.jp/services/api/AuctionGenreId/Search/20120927
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
auctionGenreId<br>*Auction Genre ID* | integer | Required | Genre ID to get information from.<br>Please use <code>0</code> for the root genre.
genrePath<br>*Genre path* | integer | Optional | Whether or not to include genre ancestors information in the response.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/AuctionGenreId/Search/20120927?applicationId=REPLACE_WITH_YOUR_APP_ID&auctionGenreId=1150000000
##### Response

```json
{
  "current": {
    "auctionGenreId": "1150000000",
    "genreName": "本・雑誌・コミック",
    "fullGenrePath": "本・雑誌・コミック",
    "genreLevel": 1,
    "hasChildFlg": 1,
    "ngRegistFlg": 1
  },
  "children": [
    {
      "child": {
        "auctionGenreId": "1150000010",
        "genreName": "漫画・コミック",
        "fullGenrePath": "本・雑誌・コミック >> 漫画・コミック",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150012740",
        "genreName": "写真集",
        "fullGenrePath": "本・雑誌・コミック >> 写真集",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150023360",
        "genreName": "詩集・句集 ",
        "fullGenrePath": "本・雑誌・コミック >> 詩集・句集 ",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150019240",
        "genreName": "ライフスタイル",
        "fullGenrePath": "本・雑誌・コミック >> ライフスタイル",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150019400",
        "genreName": "ホビー・スポーツ・美術",
        "fullGenrePath": "本・雑誌・コミック >> ホビー・スポーツ・美術",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150018590",
        "genreName": "資格・検定",
        "fullGenrePath": "本・雑誌・コミック >> 資格・検定",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150022140",
        "genreName": "エッセイ・随筆",
        "fullGenrePath": "本・雑誌・コミック >> エッセイ・随筆",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021090",
        "genreName": "科学・医学・技術",
        "fullGenrePath": "本・雑誌・コミック >> 科学・医学・技術",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021220",
        "genreName": "エンターテインメント",
        "fullGenrePath": "本・雑誌・コミック >> エンターテインメント",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021580",
        "genreName": "ライトノベル",
        "fullGenrePath": "本・雑誌・コミック >> ライトノベル",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021540",
        "genreName": "その他",
        "fullGenrePath": "本・雑誌・コミック >> その他",
        "genreLevel": 2,
        "hasChildFlg": 0,
        "ngRegistFlg": 0
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021430",
        "genreName": "洋書",
        "fullGenrePath": "本・雑誌・コミック >> 洋書",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021420",
        "genreName": "稀覯本・絶版本・レトロ書籍",
        "fullGenrePath": "本・雑誌・コミック >> 稀覯本・絶版本・レトロ書籍",
        "genreLevel": 2,
        "hasChildFlg": 0,
        "ngRegistFlg": 0
      }
    },
    {
      "child": {
        "auctionGenreId": "1150001000",
        "genreName": "雑誌",
        "fullGenrePath": "本・雑誌・コミック >> 雑誌",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150001270",
        "genreName": "文学・小説",
        "fullGenrePath": "本・雑誌・コミック >> 文学・小説",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020070",
        "genreName": "語学・学習参考書",
        "fullGenrePath": "本・雑誌・コミック >> 語学・学習参考書",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020000",
        "genreName": "絵本・児童書・図鑑",
        "fullGenrePath": "本・雑誌・コミック >> 絵本・児童書・図鑑",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020380",
        "genreName": "旅行・留学・アウトドア",
        "fullGenrePath": "本・雑誌・コミック >> 旅行・留学・アウトドア",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020930",
        "genreName": "PC・システム開発",
        "fullGenrePath": "本・雑誌・コミック >> PC・システム開発",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020690",
        "genreName": "ビジネス・経済・就職",
        "fullGenrePath": "本・雑誌・コミック >> ビジネス・経済・就職",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020500",
        "genreName": "人文・地歴・哲学・社会",
        "fullGenrePath": "本・雑誌・コミック >> 人文・地歴・哲学・社会",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    }
  ],
  "parents": [
    {
      "parent": {
        "auctionGenreId": "0",
        "genreName": "ルート",
        "fullGenrePath": "\\ ",
        "genreLevel": 0,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    }
  ]
}
```


### AuctionGenreKeyword/Search

#### Description

Gets up to 10 auction genres by keyword.
#### Resource URL

https://app.rakuten.co.jp/services/api/AuctionGenreKeyword/Search/20120927
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
keyword<br>*Genre keywords* | string | Required | Please encode the string using UTF-8.<br>Please enter between 2 and 128 characters. <br>You can use spaces for separating multiple keywords.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/AuctionGenreKeyword/Search/20120927?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=硬貨
##### Response

```json
{
  "auctionGenreList": [
    {
      "auctionGenreId": "1130029020",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> 日本"
    },
    {
      "auctionGenreId": "1130032510",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> 外国 >> ﾖｰﾛｯﾊﾟ"
    },
    {
      "auctionGenreId": "1130032490",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> 外国 >> ｱｼﾞｱ"
    },
    {
      "auctionGenreId": "1130032520",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> 外国 >> 北ｱﾒﾘｶ"
    },
    {
      "auctionGenreId": "1130022340",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 記念ﾒﾀﾞﾙ･ｺｲﾝ"
    },
    {
      "auctionGenreId": "1130032540",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> 外国 >> ｵｾｱﾆｱ"
    },
    {
      "auctionGenreId": "1190005320",
      "fullGenrePath": "ﾁｹｯﾄ･金券 >> その他"
    },
    {
      "auctionGenreId": "1130029030",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> 外国 >> その他"
    },
    {
      "auctionGenreId": "1130022330",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> その他"
    },
    {
      "auctionGenreId": "1130022300",
      "fullGenrePath": "おもちゃ･ﾎﾋﾞｰ･ｺﾚｸｼｮﾝ >> ｺﾚｸｼｮﾝ >> 貨幣 >> 硬貨 >> その他"
    }
  ]
}
```


### AuctionItem/Search

#### Description

Gets up to 30 auction items by keyword or auction genre id.
#### Resource URL

https://app.rakuten.co.jp/services/api/AuctionItem/Search/20130110
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

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
postageFreeFlag <br>*Free shipping flag* | integer | Optional |
closedFlag<br>*Closed exclusion flag* | integer | Optional |
bidStatus<br>*Bid status* | integer | Optional |
field<br>*Search field* | integer | Optional |
carrier<br>*Platform* | integer | Optional | Whether to return information to be displayed on PC or mobile.
imageFlag<br>*Product Image Available flag* | integer | Optional |
orFlag<br>*OR Search flag* | integer | Optional | When multiple keywords are entered, you can choose between doing an AND search or an OR search.<br>※ However, complex search conditions cannot be used, such as (A OR B) AND C.
NGKeyword<br>*Negative Keywords* | string | Optional | Keywords to exclude from search results.<br>UTF-8 encoded string.<br>Same format as the keyword parameter.
noticeIcon<br>*Notice Icon* | string | Optional | You can select multiple options using a comma-separated list.<br>Example: <code>0,1,2</code>
genreInformationFlag<br>*Genre information flag * | integer | Optional |
autoPriceDownFlag<br>*Auto Price Down Flag* | integer | Optional |
priceDownExecFlag<br>*Price cut flag* | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/AuctionItem/Search/20130110?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=郵便切手&hits=3
##### Response

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


## Rakuten Kobo

![Rakuten Kobo](https://media.antoniotajuelo.com/rakuten/service/logo/kobo.png)
* **Name** Rakuten Kobo
* **URL** https://www.kobo.com/
* **Description** Rakuten's e-book reader and bookstore.

### Kobo/GenreSearch

#### Description

Gets a Kobo genre's attributes, children genres and ancestor genres by Kobo genre id.
#### Resource URL

https://app.rakuten.co.jp/services/api/Kobo/GenreSearch/20131010
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
koboGenreId<br>*Kobo Genre ID* | string | Optional | Kobo genre ID.<br>koboGenreId = 101 is the parent genre.
genrePath<br>*Genre path* | integer | Optional | Whether or not to include a the ancestor genres in the result set:
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Kobo/GenreSearch/20131010?applicationId=REPLACE_WITH_YOUR_APP_ID&koboGenreId=101901
##### Response

```json
{
  "current": {
    "koboGenreId": "101901",
    "koboGenreName": "小説・エッセイ",
    "genreLevel": 2
  },
  "children": [
    {
      "child": {
        "koboGenreId": "101901001",
        "koboGenreName": "小説",
        "genreLevel": 3
      }
    },
    {
      "child": {
        "koboGenreId": "101901002",
        "koboGenreName": "エッセイ",
        "genreLevel": 3
      }
    },
    {
      "child": {
        "koboGenreId": "101901003",
        "koboGenreName": "ロマンス",
        "genreLevel": 3
      }
    },
    {
      "child": {
        "koboGenreId": "101901004",
        "koboGenreName": "ホラー",
        "genreLevel": 3
      }
    },
    {
      "child": {
        "koboGenreId": "101901005",
        "koboGenreName": "SF",
        "genreLevel": 3
      }
    },
    {
      "child": {
        "koboGenreId": "101901006",
        "koboGenreName": "ファンタジー",
        "genreLevel": 3
      }
    },
    {
      "child": {
        "koboGenreId": "101901007",
        "koboGenreName": "その他",
        "genreLevel": 3
      }
    }
  ],
  "parents": [
    {
      "parent": {
        "koboGenreId": "101",
        "koboGenreName": "電子書籍",
        "genreLevel": 1
      }
    }
  ]
}
```


### Kobo/EbookSearch

#### Description

Gets up to 30 Kobo items by keyword, title, author, publisher, item number or genre.
#### Resource URL

https://app.rakuten.co.jp/services/api/Kobo/EbookSearch/20140811
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
keyword<br>*Keyword* | string | At least one is required | Search for keyword.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.
title<br>*Book title* | string | At least one is required | Search for book title.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.
author<br>*Author's name* | string | At least one is required | Search for author's name.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.
publisherName<br>*Publisher* | string | At least one is required | Search for publisher's name.<br>UTF-8 encoded string.<br>If you want to search from multiple keyword they must be separated by a space.
itemNumber<br>*Item Number* | string | At least one is required | Search for item number.
koboGenreId<br>*Kobo Genre ID* | string | At least one is required | ID for identifying the genre in Rakuten Kobo<br>(Please note that this ID is different from the Rakuten Ichiba genre ID)<br>Parent is KoboGenreId = 101 (e-book).<br>If you want to browse the Genre structure, please use the "Rakuten Kobo genre search API (Kobo/GenreSearch)".
language<br>*Language* | string | Optional | It is possible to specify the language of the e-book
hits<br>*How many results per page* | integer | Optional | Integer 1 to 30.
page<br>*Result page* | integer | Optional | Integer 1 to 100.
sort<br>*Sort* | string | Optional | ※ Please use UTF-8 encoded parameters.
NGKeyword<br>*Negative Keywords* | string | Optional | Keywords that you want to exclude from search query.
field<br>*Search field* | integer | Optional |
orFlag<br>*OR search flag* | integer | Optional | When multiple keywords are set it defaults for AND operator search, but you can switch to OR operator mode.
genreInformationFlag<br>*Genre information flag * | integer | Optional |
salesType<br>*Sales Type* | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Kobo/EbookSearch/20140811?applicationId=REPLACE_WITH_YOUR_APP_ID&author=村上春樹&hits=3
##### Response

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


## Rakuten GORA

![Rakuten GORA](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-gora.png)
* **Name** Rakuten GORA
* **URL** http://gora.golf.rakuten.co.jp/
* **Description** Rakuten's online golf reservation site.

### Gora/GoraGolfCourseSearch

#### Description

Gets up to 30 golf courses.
#### Resource URL

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseSearch/20131113
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
keyword<br>*Search keywords* | string | Optional | UTF-8 encoded string.
areaCode<br>*Area code* | integer | Optional | Code used to identify the area in Rakuten GORA.<br>If you want to examine the area code, please refer to the "Rakuten GORA Area Code List".
latitude<br>*Latitude* | decimal | Optional | Please enter in Japan datum
longitude<br>*Longitude* | decimal | Optional | Please enter in Japan datum
searchRadius<br>*Search Radius* | integer | Optional | Latitude and longitude radius when searching (in km)<br>It can be specified between a radius of 10 ~ 300km
hits<br>*How many results to display on each page* | integer | Optional | Integer of 1-30
page<br>*Result page* | integer | Optional | Integer of 1-100
sort<br>*Sort* | string | Optional |
reservation<br>*Booking* | integer | Optional |
carrier<br>*Platform* | integer | Optional | Whether to return information for PC or mobile phones.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseSearch/20131113?applicationId=REPLACE_WITH_YOUR_APP_ID&hits=3
##### Response

```json
{
  "count": 1935,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 645,
  "Items": [
    {
      "Item": {
        "golfCourseId": 80004,
        "golfCourseName": "アジア取手カントリー倶楽部",
        "golfCourseAbbr": "アジア取手CC",
        "golfCourseNameKana": "あじあとりでかんとりーくらぶ",
        "golfCourseCaption": "常磐道の谷和原I.C.より15分！都心からのアクセスの良さが魅力。姉妹コースに続き、【セグウェイ】を100台導入！日本一の導入数を誇ります。フェアウェイ乗り入れ可能で移動も快適、【セグウェイでゴルフ】を是非体験してみて下さい。\n\n【お得プランの一部をご紹介】\n・全日廻り放題！＊当日の天候、日没状況により、追加ラウンドできない場合もございます。\n・お誕生月特典あり！\n・平日は食べ放題のランチバイキング、4サム割引きあり。\nお得で楽しい一日をお気軽にお過ごし下さい。",
        "address": "茨城県取手市稲1340",
        "latitude": 35.9061664,
        "longitude": 140.0397556,
        "highway": "常磐自動車道谷和原",
        "golfCourseDetailUrl": "http://booking.gora.golf.rakuten.co.jp/guide/disp/c_id/80004",
        "reserveCalUrl": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/80004",
        "ratingUrl": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/80004",
        "golfCourseImageUrl": "http://gora.golf.rakuten.co.jp/img/golf/80004/photo1.jpg",
        "evaluation": 3.3
      }
    },
    {
      "Item": {
        "golfCourseId": 90076,
        "golfCourseName": "那須小川ゴルフクラブ",
        "golfCourseAbbr": "那須小川GC",
        "golfCourseNameKana": "なすおがわごるふくらぶ",
        "golfCourseCaption": "鮎で有名な那珂川町にあるゴルフ場です。開場４５周年目を迎え『ドキドキ・ワクワク』できる場を提供すべく日々邁進します！\n\nコースは合計２１ホール。\nトーナメントコースの１８ホール、那須小川レディスプロトーナメントを開催していました。その由来で名付けています。コースコンセプトは『ちょい難』。那須小川のプレーで鍛えるとスコアが良くなる！そんなコース造りをしています。グリーンは通称『F1グリーン』、オンシーズンは１０feat以上の時もあり速いですよ～。ちょっと難しいコースに挑戦するあなたは素敵です！\nその他練習ホールの『プラス３』があります。\n\n『知ってますか？那須小川のランチバイキングは･･･\nカニ食放題をはじめ、５０種類の品揃えはすべて食放題＆アルコールを含むドリンク２０種類も飲放題・◯―ル、ワ◯ン、日本◯、も！さらに朝食はサービス（９時迄、９時～９時３０分はカレータイム）。午後はスイーツタイム（１６時迄）６種のアイスが無料でいただけます。だから、少し早めのご来場と乗り合いを推奨します。楽しいゴルフ仲間と朝食から夕方までゴルフライフを楽しみましょう！\n\nアクセスは正直良くありません。秘湯ならぬ秘ゴルフ場を目指します（笑）。そこで、宿泊プランはとってもお得にしています、ちょっと覗いてください。\n\n食事だけ・泊りだけ・何となく寄っただけ、でもウエルカム！みなさんの“楽しい”に寄り添う那須小川ＧＣです。",
        "address": "栃木県那須郡那珂川町三輪1283",
        "latitude": 36.7489853,
        "longitude": 140.0990356,
        "highway": "東北自動車道矢板",
        "golfCourseDetailUrl": "http://booking.gora.golf.rakuten.co.jp/guide/disp/c_id/90076",
        "reserveCalUrl": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/90076",
        "ratingUrl": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/90076",
        "golfCourseImageUrl": "http://gora.golf.rakuten.co.jp/img/golf/90076/photo1.jpg",
        "evaluation": 4.2
      }
    },
    {
      "Item": {
        "golfCourseId": 280065,
        "golfCourseName": "三田レークサイドカントリークラブ",
        "golfCourseAbbr": "三田レークサイドCC",
        "golfCourseNameKana": "さんだれーくさいどかんとりーくらぶ",
        "golfCourseCaption": "　全カート、『リモコン操作の電磁誘導5人乗りカート』を導入。さらに『ＧＰＳナビゲーション』付です。わずらわしいカートの移動も無くプレーに集中出来き大変好評です。またコースメンテナンスも高い評価を頂戴いたしております。\n「来て良かった。また来るよ」と言って頂ける価値の高いコストパフォーマンス。GORA予約ランキング第１位・2012年西日本の部は安心の証です。",
        "address": "兵庫県三田市大川瀬1461",
        "latitude": 34.9436875,
        "longitude": 135.1140517,
        "highway": "中国自動車道吉川",
        "golfCourseDetailUrl": "http://booking.gora.golf.rakuten.co.jp/guide/disp/c_id/280065",
        "reserveCalUrl": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/280065",
        "ratingUrl": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/280065",
        "golfCourseImageUrl": "http://gora.golf.rakuten.co.jp/img/golf/280065/photo1.jpg",
        "evaluation": 3.9
      }
    }
  ]
}
```


### Gora/GoraGolfCourseDetail

#### Description

Gets a golf course details by a golf course id.
#### Resource URL

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseDetail/20140410
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
golfCourseId<br>*Golf course ID* | long | Required | You can get this value from the output of Rakuten GORA golf Search API (GoraGolfCourceSearch)
carrier<br>*Platform* | integer | Optional | Whether to request information for PC or mobile phone usage:
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseDetail/20140410?applicationId=REPLACE_WITH_YOUR_APP_ID&golfCourseId=80004
##### Response

```json
{
  "Item": {
    "carrier": 0,
    "golfCourseId": 80004,
    "golfCourseName": "アジア取手カントリー倶楽部",
    "golfCourseAbbr": "アジア取手CC",
    "golfCourseNameKana": "あじあとりでかんとりーくらぶ",
    "golfCourseCaption": "常磐道の谷和原I.C.より15分！都心からのアクセスの良さが魅力。姉妹コースに続き、【セグウェイ】を100台導入！日本一の導入数を誇ります。フェアウェイ乗り入れ可能で移動も快適、【セグウェイでゴルフ】を是非体験してみて下さい。\n\n【お得プランの一部をご紹介】\n・全日廻り放題！＊当日の天候、日没状況により、追加ラウンドできない場合もございます。\n・お誕生月特典あり！\n・平日は食べ放題のランチバイキング、4サム割引きあり。\nお得で楽しい一日をお気軽にお過ごし下さい。",
    "information": "【20歳代限定無料レンタルクラブ企画参加コースです】\n☆20～29歳の方限定でレンタルクラブを無料でお貸出しします。\nhttp://gora.golf.rakuten.co.jp/doc/rakugol/?tp=heaader_rakugol\n【予約方法】\n(1)ゴルフ場予約完了後、ゴルフ場に電話（プレー3日前まで）\n(2)「楽ゴルを見た！！」と伝え、レンタルクラブの利用人数と性別をお伝え下さい。\n(3)当日受付時に学生証や免許証等、年齢を確認できるものを提示下さい。\n(4)プレー前後にゴルフ場のスタッフとクラブ本数をご確認下さい。\n\n【★必読★】下記ご確認の上、お申込下さい\n※20～29歳限定のサービスです。\n※早朝プランなどレンタルクラブ利用不可のプランもございます。予約時にゴルフ場に必ずご確認下さい。\n※予約完了後、プレー3日前までにレンタルクラブ利用希望の旨をゴルフ場にお電話下さい。\n※レンタルクラブは数に限りがあるため利用できない場合があります。なるべくお早めにゴルフ場にお電話下さい。\n※3日前を過ぎてからのご予約の場合、レンタルクラブの貸出しはできません。\n※当日、年齢を確認できるものを提示されない場合、または20歳代でない場合は有料になります。\n※レンタルクラブのメーカーは指定できませんので予めご了承下さい。\n\n\n+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-+:-+:-+:-+:-++:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-:+:-+:-+:-+:-+:-+\n\n\n※２か月前の１日よりご予約を承っております。\n　例）１０月のご予約は８月１日よりご予約可能です。\n\n☆ＪＲ取手駅よりクラブバスが運行\n\n　　平日：毎時０５、３５分 （要予約）\n\n　　土日：毎時１０、３０，５０分。\n\n＜クラブバス乗車位置＞\n取手駅西口を出て、線路沿いに左・東京方面へ進むと有料駐車場があります。その前が乗車位置となります。\n\n\n☆浴室は檜風呂になります。\n\n☆全て乗用カートセルフプレー。カードはご利用になれません。\n\n\n\n【ご来場にあたってのお願い】\n\n◎乗用カートの走行は、カート道のみでお願いします。\n\n◎喫煙は所定の場所でお願いします。\n\n◎ゴルフバッグの積み下ろしは、基本的にセルフでお願いします。\n\n◎遅延プレー者及び、マナーが悪く注意された場合は、追加ラウンドをお断りいたします。\n\n\n皆さまのご協力により、廻り放題が成り立っております。ご理解くださいますようお願いいたします。\n新しくゴルファーになるお仲間にもマナーなど楽しくラウンドできるように教えてあげてくださいね！！\n\n\n\n皆様のご来場をお待ちしております。。。",
    "highway": "常磐自動車道",
    "ic": "谷和原",
    "icDistance": "10km以内",
    "latitude": "35.9061664",
    "longitude": "140.0397556",
    "postalCode": "302-0026",
    "address": "茨城県取手市稲1340",
    "telephoneNo": "0297-72-0727",
    "faxNo": "0297-72-0795",
    "openDay": "1964-10-03",
    "closeDay": "",
    "creditCard": "現金のみ",
    "shoes": "指定なし",
    "dressCode": "",
    "practiceFacility": "なし",
    "lodgingFacility": "なし",
    "otherFacility": "カート：乗用カート　乗入れ不可\n　　　　セグウェイ　乗入れ可\n\n20歳代限定レンタルクラブ無料\n※利用制限・注意事項有（楽天GORA内[楽ゴル]ページ及びゴルフ場に直接ご確認下さい）",
    "golfCourseImageUrl1": "http://gora.golf.rakuten.co.jp/img/golf/80004/photo1.jpg",
    "golfCourseImageUrl2": "http://gora.golf.rakuten.co.jp/img/golf/80004/photo2.jpg",
    "golfCourseImageUrl3": "http://gora.golf.rakuten.co.jp/img/golf/80004/photo3.jpg",
    "golfCourseImageUrl4": "http://gora.golf.rakuten.co.jp/img/golf/80004/photo4.jpg",
    "golfCourseImageUrl5": "http://gora.golf.rakuten.co.jp/img/golf/80004/photo5.jpg",
    "weekdayMinPrice": 3100,
    "baseWeekdayMinPrice": 2593,
    "holidayMinPrice": 7000,
    "baseHolidayMinPrice": 6019,
    "designer": "浅見　緑蔵",
    "courseType": "河川",
    "courseVerticalInterval": "フラット",
    "dimension": "89万m2",
    "green": "高麗",
    "greenCount": "2グリーン",
    "holeCount": 27,
    "parCount": 108,
    "courseName": "OUT・IN・西コース",
    "courseDistance": "9458Y",
    "longDrivingContest": "",
    "nearPin": "",
    "ratingNum": 18496,
    "evaluation": 3.3,
    "staff": 3.3,
    "facility": 2.7,
    "meal": 3.3,
    "course": 3,
    "costperformance": 3.8,
    "distance": 3.1,
    "fairway": 3.3,
    "reserveCalUrl": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/80004",
    "voiceUrl": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/80004",
    "layoutUrl": "http://booking.gora.golf.rakuten.co.jp/guide/layout_disp/c_id/80004",
    "routeMapUrl": "http://booking.gora.golf.rakuten.co.jp/guide/map/c_id/80004",
    "newPlans": [
      {
        "plan": {
          "month": "4月",
          "planName": "[春コンペ]3組9名～☆セルフ☆昼食＆1D付",
          "planDate": "平日",
          "service": "乗用カートセルフ昼食付",
          "price": "6,200",
          "basePrice": 0,
          "salesTax": 422,
          "courseUseTax": 400,
          "otherTax": 100
        }
      },
      {
        "plan": {
          "month": "2月",
          "planName": "[早得]セグウェイセルフ☆昼食付☆誕生月特典有",
          "planDate": "平日",
          "service": "セルフ昼食付",
          "price": "6,500",
          "basePrice": 0,
          "salesTax": 444,
          "courseUseTax": 400,
          "otherTax": 100
        }
      },
      {
        "plan": {
          "month": "2月",
          "planName": "[早得]2月セルフ◇廻り放題・誕生月特典有",
          "planDate": "平日",
          "service": "乗用カートセルフ昼食付",
          "price": "5,200",
          "basePrice": 0,
          "salesTax": 348,
          "courseUseTax": 400,
          "otherTax": 100
        }
      }
    ],
    "ratings": [
      {
        "rating": {
          "title": "初めて利用しました(2015-12-12 12:11:34)",
          "nickName": "acri05",
          "prefecture": "神奈川県",
          "age": "40代",
          "sex": "男性",
          "times": 37,
          "evaluation": 5,
          "staff": 5,
          "facility": 3,
          "meal": 3,
          "course": 3,
          "costperformance": 5,
          "distance": 5,
          "fairway": 3,
          "comment": "平日でしたが混んでいて毎ホール待たされました"
        }
      },
      {
        "rating": {
          "title": "セグウエイ快適でした(2015-11-03 14:34:49)",
          "nickName": "匿名さん",
          "prefecture": "東京都",
          "age": "",
          "sex": "",
          "times": 6,
          "evaluation": 5,
          "staff": 5,
          "facility": 5,
          "meal": 5,
          "course": 4,
          "costperformance": 4,
          "distance": 4,
          "fairway": 3,
          "comment": "初めてのセグウエイ、快適でした。お天気、同伴競技者にも恵まれ、素晴らしい一日を過ごせました。\nまた、セグウエイ、乗りたいです。"
        }
      },
      {
        "rating": {
          "title": "快適にプレーできました(2015-10-14 15:13:27)",
          "nickName": "oda1974",
          "prefecture": "千葉県",
          "age": "40代",
          "sex": "男性",
          "times": 19,
          "evaluation": 5,
          "staff": 3,
          "facility": 3,
          "meal": 3,
          "course": 3,
          "costperformance": 5,
          "distance": 4,
          "fairway": 2,
          "comment": "セグウェイでのラウンド。\n使用方法の説明も丁寧で、安全にラウンドできました。\n混雑もなく、快適でした。"
        }
      }
    ]
  }
}
```


### Gora/GoraPlanSearch

#### Description

Gets up to 30 golf courses by a date.
#### Resource URL

https://app.rakuten.co.jp/services/api/Gora/GoraPlanSearch/20150706
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
golfCourseName<br>*Golf course name* | string | Optional | UTF-8 encoded string.<br>You can search for multiple keywords by using space as separator.<br>(* 1) It is required to specify at least one of these parameters: golf course name, area code or golf course.
areaCode<br>*Area code* | integer | Optional | Code used to identify the area in Rakuten GORA<br>If you want to examine the area code list, please refer to the "Rakuten GORA Area Code List".<br>This field allows you to specify more than one in CSV format.<br>Example: <code>areaCode=1,2,3</code><br>(* 1) It is required to specify at least one of these parameters: golf course name, area code or golf course.
golfCourseId<br>*Golf course ID* | long | Optional | This field is included in the output of Rakuten GORA golf Search API (GoraGolfCourceSearch)<br>※ You can specify up to 30 values using comma as separator.<br>(* 1) It is required to specify at least one of these parameters: golf course name, area code or golf course.
playDate<br>*Play Date* | string | Required | ※ Please enter in the form of YYYY-MM-DD<br>※ If you enter a past date, the response will result in an error
hits<br>*How many results to display on each page * | integer | Optional | Integer 1 to 30
page<br>*Page number* | integer | Optional | Integer from 1 to 100
sort<br>*Sort* | string | Optional |
minPrice<br>*Play rate (minimum price)* | integer | Optional |
maxPrice<br>*Play rate (maximum price)* | integer | Optional | Up to 25,000 yen
startTimeZone<br>*Time Zone* | integer | Optional | This field allows you to specify more than one value in CSV format.<br>Example: <code>startTimeZone=5,7,9</code>
range<br>*Continuous frame specified* | integer | Optional | You can search for continuous frame of the same course<br>※ continuous frame of more than the specified number of sets will be searched
planCaddie<br>*[Plan designation] with caddy* | integer | Optional |
planCart<br>*[Plan designation] With riding cart* | integer | Optional |
planStay<br>*[Plan designation] accommodation plan* | integer | Optional |
planLunch<br>*[Plan designation] with lunch* | integer | Optional |
plan2sum<br>*[Plan designation] 2 Sum guarantee* | integer | Optional |
planDiscount4sum<br>*[Plan designation] 4 Sum discount* | integer | Optional |
planAdd1RFree<br>*[Plan designation] Additional 1R Free* | integer | Optional |
planAddHalfFree<br>*[Plan designation] Additional 0.5R Free* | integer | Optional |
planNoAddFee2b<br>*[Plan designation] 2B no additional charge* | integer | Optional |
planNoAddFee3b<br>*[Plan designation] 3B no additional charge* | integer | Optional |
planDrink<br>*[Plan designation] 1 drink* | integer | Optional |
planGoraOrg<br>*[Plan designation] GORA limited* | integer | Optional |
planLesson<br>*[Plan designation] lessons* | integer | Optional |
planOpenCompe<br>*[Plan designation] open competition* | integer | Optional |
planHalfRound<br>*[Plan designation] 9H play* | integer | Optional |
planEarly<br>*[Plan designation] early morning play* | integer | Optional |
NGPlan<br>*[Plan designation] Plan search exclusion (negative keywords)* | string | Optional | You can specify more than one in CSV format.<br>Example: <code>NGPlan=planCart,planLesson,planHalfRound</code><br>* we changed planLesson, from <code>planCompe</code> to <code>planOpenCompe</code>.
courseType<br>*Course type* | integer | Optional |
shapeWideFairway<br>*[Course shape] fairway is wide* | integer | Optional |
shapeLessOB<br>*[Course shape] shape is less OB* | integer | Optional |
practiceFacility<br>*[Private] There practice field* | integer | Optional |
lodgingFacility<br>*[Facility] There accommodation* | integer | Optional |
onsenFacility<br>*[Facility] There Onsen* | integer | Optional |
highwayCode<br>*Highway code* | integer | Optional | Code used to identify the highway in Rakuten GORA<br>If you want to examine the highway code, the "Rakuten GORA highway code list" Please refer to<br>※ If there is no area specified, but can be narrowed down in all of the highway code, if the area is specified, the highway code that can be specified is different depending on the area, please note
icDistance<br>*Distance from the interchange* | integer | Optional |
pointFlag<br>*Point gift flag* | integer | Optional |
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Gora/GoraPlanSearch/20150706?applicationId=REPLACE_WITH_YOUR_APP_ID&playDate=2016-02-05&hits=3
##### Response

```json
{
  "count": 1721,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "pageCount": 100,
  "Items": [
    {
      "Item": {
        "golfCourseId": 100016,
        "golfCourseName": "関越ハイランドゴルフクラブ",
        "golfCourseCaption": "雄大な景観豊かな自然を生かした個性的な27ホール。\nカエデコースは､フラットな林間コースの趣で､自然を巧みにとり入れたレイアウト。\nフェアウェイは､広く豪快なドライバーショットでダイナミックなゴルフが存分に堪能できます。\nケヤキコースは､ロングホールが多く､池の配置とグリーン周りのバンカーが引き締める変化に富んだタフなコース。\nフェアウェイの幅をたっぷり伸び伸びプレーがお楽しみいただけます。\nサザンカコースは､大きく深いバンカーにガードされたグリーンは､チャレンジ精神を掻き立てられます。\n距離はさほど出ないが大きくゆったりとドッグレッグしたホールなど戦略的なコースです。",
        "golfCourseRsvType": 1,
        "areaCode": 10,
        "prefecture": "群馬県",
        "highwayCode": 11271,
        "highway": "上信越自動車道",
        "ic": "吉井",
        "icDistance": "5km以内",
        "golfCourseImageUrl": "http://booking.gora.golf.rakuten.co.jp/img/golf/100016/photo1.jpg",
        "displayWeekdayMinPrice": "平日 3,070円（2288円＋税）～",
        "displayWeekdayMinBasePrice": "平日 2,288円（総額 3,070円）～",
        "displayHolidayMinPrice": null,
        "displayHolidayMinBasePrice": null,
        "cancelFeeFlag": 0,
        "cancelFee": "",
        "ratingNum": 6303,
        "evaluation": 3.7,
        "reserveCalUrlPC": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/100016/",
        "reserveCalUrlMobile": "http://gr.g.rakuten.co.jp/b/?menu=mbl_cal&act=disp&c_id=100016",
        "ratingUrlPC": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/100016",
        "ratingUrlMobile": "http://gr.g.rakuten.co.jp/b/?menu=mbl_voice&act=detail&c_id=100016",
        "planInfo": [
          {
            "plan": {
              "planId": 5280895,
              "planName": "薄暮９Ｈプレー☆割増無料＆2Ｂ保証",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 3070,
              "basePrice": 2288,
              "salesTax": 182,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "0.5R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 0,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "※以下の点につきまして予めご了承の程お願い申し上げます。\n\n◆スタート時間及びコースは当日の状況により多少前後する場合がございますので予めご了承ください。\n◆ロッカー、浴場はご利用いただけません。\n◆当日の状況により、日没によるプレー終了をさせて頂く場合がございます。その際、返金等の割引はございません。\n\n※プレー当日に直接ゴルフ場へご連絡いただき、スタート時間のご確認をおすすめしております。\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 9,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5280895/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5280895&stock_id=&date=20160205&s_pd=100016;5280895"
              }
            }
          },
          {
            "plan": {
              "planId": 5280900,
              "planName": "[コンペＣＰ]４組１３名様以上で幹事様無料！昼食付",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 4590,
              "basePrice": 3695,
              "salesTax": 295,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 4,
              "compePlayMemberMin": 13,
              "compePrivilegeFree": "４組１３名様からのお申込みで＜予約代表者１名様無料＞\n\n※無料プレー対象者様は以下が実費となります。\n　ゴルフ場利用税600円・昼食代・その他の飲食代等\n※本プランは４組１３名以上から予約可\n※プレー当日に規定人数に満たなかった場合は１名無料は対象外となります。\n\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": "☆パーティパック\nお一人様別途＋1,620円で以下のパーティパックをご用意させて頂きます。\n★料理４～５品程度\n★ソフトドリンク飲み放題\n（コーラ・ウーロン茶・ジュースピッチャー対応）\n※飲み放題につきましては、乾杯より９０分間とさせて頂いております。\n※ご希望のお客様は必ず事前にご予約をお願い致します。\n※パーティー会場は､レストランの一角でのご案内となる場合がございます。",
              "other": "※他の優待との併用は出来ません。\n※当クラブは３コース２７Ｈとなっておりますので、以下の内容を必ず事前にご確認ください。\n◇スタートコースを分けた場合において、ＯＵＴ/ＩＮ等の同一１８ホールプレー及び集計は承ることが出来ません。\n◇ラウンドコースのローテーションは、以下の通り固定となっております。\n　かえで　⇒　さざんか　⇒　けやき　⇒ かえで\n※上記によりまして、コンペのご案内につきましては以下のご案内を推奨しております。\n◇３～７組　同一コースよりスタート\n◇８組以上　３コースより同時間帯からのスタート",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 67,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5280900/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5280900&stock_id=&date=20160205&s_pd=100016;5280900"
              }
            }
          },
          {
            "plan": {
              "planId": 5280935,
              "planName": "[コンペＣＰ]得々コンペパック☆昼食＆ワンドリンク付",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 4790,
              "basePrice": 3880,
              "salesTax": 310,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 1,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 3,
              "compePlayMemberMin": 10,
              "compePrivilegeFree": "◇お得なワンドリンク付コンペプラン\n◇サービスのワンドリンクは昼食時のご提供となります。ドリンクパーティへの変更は承りません。\n◇サービスのワンドリンクは生ビール（グラス）、酎ハイ等のアルコール類のご提供も承っております。\n\n※パーティ、表彰式については、別途ご予算が必要となります。\n※お車でご来場のお客様はソフトドリンンクのご提供となります。\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": "☆パーティパック\nお一人様別途＋1,620円で以下のパーティパックをご用意させて頂きます。\n★料理４～５品程度\n★ソフトドリンク飲み放題\n（コーラ・ウーロン茶・ジュースピッチャー対応）\n※飲み放題につきましては、乾杯より90分間とさせて頂いております。\n※ご希望のお客様は必ず事前にご予約をお願い致します。\n※パーティー会場は､レストランの一角でのご案内となる場合がございます。",
              "other": "※他の優待との併用は出来ません。\n※当クラブは３コース２７Ｈとなっておりますので、以下の内容を必ず事前にご確認ください。\n◇スタートコースを分けた場合において、ＯＵＴ/ＩＮ等の同一１８ホールプレー及び集計は承ることが出来ません。\n◇ラウンドコースのローテーションは、以下の通り固定となっております。\n　かえで　⇒　さざんか　⇒　けやき　⇒ かえで\n※上記によりまして、コンペのご案内につきましては以下のご案内を推奨しております。\n◇３～７組　同一コースよりスタート\n◇８組以上　３コースより同時間帯からのスタート",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 67,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5280935/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5280935&stock_id=&date=20160205&s_pd=100016;5280935"
              }
            }
          },
          {
            "plan": {
              "planId": 5340001,
              "planName": "[Sale][割増なし]早めスタート限定☆昼付＆2B無料",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 4790,
              "basePrice": 3880,
              "salesTax": 310,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "☆ＧＯＲＡマンスリーセール\n早めスタート限定特別優待！！\n\nさらに！！\n2Ｂ保証＆割増無料！！\n\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 21,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5340001/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5340001&stock_id=&date=20160205&s_pd=100016;5340001"
              }
            }
          },
          {
            "plan": {
              "planId": 5280968,
              "planName": "[Sale][割増なし]１２時台午後スルー☆昼食＆練習場付",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 4990,
              "basePrice": 4065,
              "salesTax": 325,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "練習ボール２４球プレゼント！！\n\n以下につきまして、必ず事前のご確認をお願い致します。\n◆受付開始時間 10：00～\n◆当日の状況により【スタート時間/コース】につきまして、事前の告知なく変更させて頂く場合がございます。\nお時間のゆとりを持ってご来場ください。\n◆練習場のご利用開始は10：30からになります。\n◆サービスのご昼食はスタート前に必ずご利用下さい。ご昼食を摂らない場合の割引はございません。\nスタート時間45分前までにレストランにお起こしください。\n尚、お時間を厳守頂けなかった場合、ご昼食をご提供出来ない場合がございます。その際も割引はございません。\n◆プレー終了後のレストランはご利用できません。\n◆お風呂・ロッカー等の付随施設は全てご利用頂けます。\n◆ご精算はスタート前にお願い致します。（クレジット可）\n◆スコア集計は承っておりますが、パーティーのご用意はできません。また、表彰式会場のご用意もできません。\n\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 9,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5280968/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5280968&stock_id=&date=20160205&s_pd=100016;5280968"
              }
            }
          },
          {
            "plan": {
              "planId": 5340003,
              "planName": "[Sale][割増なし]遅めスタート限定☆昼付＆2B無料",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 4990,
              "basePrice": 4065,
              "salesTax": 325,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "☆ＧＯＲＡマンスリーセール\n遅めスタート限定特別優待！！\n\nさらに！！\n2Ｂ保証＆割増無料！！\n\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 30,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5340003/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5340003&stock_id=&date=20160205&s_pd=100016;5340003"
              }
            }
          },
          {
            "plan": {
              "planId": 5340011,
              "planName": "[Sale][割増なし]プライムタイム限定☆昼付＆2B無料",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 5190,
              "basePrice": 4250,
              "salesTax": 340,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "☆ＧＯＲＡマンスリーセール\nプライムタイムスタート限定特別優待！！\n\nさらに！！\n2Ｂ保証＆割増無料！！\n\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 16,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5340011/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5340011&stock_id=&date=20160205&s_pd=100016;5340011"
              }
            }
          },
          {
            "plan": {
              "planId": 5340018,
              "planName": "[Sale]早め1.5Ｒ保証＆27Ｈ制覇☆昼食付＆2B無料",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 5290,
              "basePrice": 4343,
              "salesTax": 347,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1.5R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "☆ＧＯＲＡマンスリーセール\n早めスタート限定！！1.5Ｒ27Ｈ制覇！！\n\nさらに！！\n2Ｂ保証＆割増無料！！\n\n◆以下につきましては、予めご了承の程お願い致します。\n※前半9Ｈ終了後、昼食休憩となります。\n※18Ｈスループレーでのご用意は出来ません。\n※当日の状況により18Ｈ終了後休憩を取って頂く場合がございます。\n※当日の状況により日没となる可能性がございます。\n　その際に返金・割引等はございません。\n※お客様のご都合による18Ｈで終了された場合も返金・割引等はございません。\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 21,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5340018/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5340018&stock_id=&date=20160205&s_pd=100016;5340018"
              }
            }
          },
          {
            "plan": {
              "planId": 5280888,
              "planName": "冬季優待料金☆昼食付・2Ｂ保証",
              "planType": 2,
              "limitedTimeFlag": 0,
              "price": 6000,
              "basePrice": 5000,
              "salesTax": 400,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 1,
              "addFee2b": 540,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "※2Ｂ時540円の追加料金がございます。\n※他の優待との併用は出来ません。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 67,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5280888/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5280888&stock_id=&date=20160205&s_pd=100016;5280888"
              }
            }
          },
          {
            "plan": {
              "planId": 5280943,
              "planName": "[コンペCP]楽々コンペパック☆昼食＆パーティ付",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 6090,
              "basePrice": 5084,
              "salesTax": 406,
              "courseUseTax": 600,
              "otherTax": 0,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 3,
              "compePlayMemberMin": 10,
              "compePrivilegeFree": "☆お得なパーティー1,620円相当付コンペプラン\n★料理４～５品程度\n★ソフトドリンク飲み放題\n（コーラ・ウーロン茶・ジュースピッチャー対応）\n※飲み放題につきましては、乾杯より９０分間とさせて頂いております。\n※パーティー会場は､レストランの一角でのご案内となる場合がございます。\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": null,
              "other": "※他の優待との併用は出来ません。\n※当クラブは３コース２７Ｈとなっておりますので、以下の内容を必ず事前にご確認ください。\n◇スタートコースを分けた場合において、ＯＵＴ/ＩＮ等の同一１８ホールプレー及び集計は承ることが出来ません。\n◇ラウンドコースのローテーションは、以下の通り固定となっております。\n　かえで　⇒　さざんか　⇒　けやき　⇒ かえで\n※上記によりまして、コンペのご案内につきましては以下のご案内を推奨しております。\n◇３～７組　同一コースよりスタート\n◇８組以上　３コースより同時間帯からのスタート\n\n【キャンセル料について】\n土日祝のキャンセルにつきましてはキャンセル料を申し受け致します。\n尚、組数・ご来場人数の減少につきましては、\nキャンセル料の対象外とさせて頂きます。\n\n2組以下のご予約　プレー日より7日前\n3組以上のご予約　プレー日より14日前　\n1組あたり×5000円（税別）",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 67,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/100016/plan_id/5280943/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=100016&plan_id=5280943&stock_id=&date=20160205&s_pd=100016;5280943"
              }
            }
          }
        ]
      }
    },
    {
      "Item": {
        "golfCourseId": 280132,
        "golfCourseName": "富士ＯＧＭゴルフクラブ小野コース",
        "golfCourseCaption": "立地条件に恵まれた兵庫県・小野市のなだらかな丘陵地に広がる富士ＯＧＭゴルフクラブ小野コース。コース設計監修を担当したアーノルド・パーマーはこの地を絶賛し、彼の理想とする素晴らしいコースを創り上げました。\n兵庫県内でも屈指のグリーンコンディションを誇る他、練習場・アプローチ・バンカー練習場も完備しており、ゴルフ好きな方にはたまらない施設が整っております。\nまた、もうひとつの自慢はお風呂！！男女問わず、サウナ・ジャグジー・露天風呂・打たせ湯を完備しており、ゴルフで疲れた身体をゆっくりと癒していただけます。\n1日を有意義に過ごせる当コースへ、是非お越しください。",
        "golfCourseRsvType": 1,
        "areaCode": 28,
        "prefecture": "兵庫県",
        "highwayCode": 11421,
        "highway": "山陽自動車道",
        "ic": "三木小野",
        "icDistance": "10km以内",
        "golfCourseImageUrl": "http://booking.gora.golf.rakuten.co.jp/img/golf/280132/photo1.jpg",
        "displayWeekdayMinPrice": "平日 7,250円（6204円＋税）～",
        "displayWeekdayMinBasePrice": "平日 6,204円（総額 7,250円）～",
        "displayHolidayMinPrice": null,
        "displayHolidayMinBasePrice": null,
        "cancelFeeFlag": 1,
        "cancelFee": "【キャンセル料】\n 　平日３日前の正午以降お一人様2,000円(総額)\n 　土日祝７日前の正午以降お一人様5,000円(総額)　頂戴します。\n 　ご予約の際はご留意くださいませ。\n 　キャンセルフィはいかなる事由においても頂戴いたします。\n\nキャンセル料は人数変更及びプレー日の変更の場合でも頂戴致しますので予めご留意ください。万が一予約者氏名が「未定」のままでも、「予約者人数」に対して「当日来場者人数」変更があった場合は、キャンセルフィの対象になります。人数変更の際は必ず設定変更もしくは事前連絡してください。\n\n※予約確定宣言プランに関しては4,000円(総額)のキャンセル料が発生いたします。",
        "ratingNum": 3425,
        "evaluation": 4.2,
        "reserveCalUrlPC": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/280132/",
        "reserveCalUrlMobile": "http://gr.g.rakuten.co.jp/b/?menu=mbl_cal&act=disp&c_id=280132",
        "ratingUrlPC": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/280132",
        "ratingUrlMobile": "http://gr.g.rakuten.co.jp/b/?menu=mbl_voice&act=detail&c_id=280132",
        "planInfo": [
          {
            "plan": {
              "planId": 5276469,
              "planName": "[早割]【7・10時台】3組～☆朝+各茶店1D+昼+特典付",
              "planType": 2,
              "limitedTimeFlag": 1,
              "price": 7250,
              "basePrice": 6204,
              "salesTax": 496,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 1,
              "addFee3b": 540,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 3,
              "compePlayMemberMin": 9,
              "compePrivilegeFree": "※コンペ特典としてボール1ダース付♪\n※5組以上ならさらに選べる賞品プレゼント♪（2,500円相当の季節のフルーツ詰合せor豚しゃぶ肉）\n●朝食バイキング・各茶店1ドリンク・昼食付♪ (昼食は1,300円を超える場合、差額を頂戴します。)\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": null,
              "other": "☆[早割]期間限定☆ \n\n☆予約期間中にご予約をされると･･･ \n\n特別限定価格で大変お得に♪ \n\n☆今がチャンス！是非ご予約を！！ \n\n※上記掲載プランの予約受付期間以降のご予約、プレー日等の変更は特典無効になりますので予めご了承下さい。 \n\n★皆様のご来場お待ちしております♪ \n\n【7・10時台限定】平日コンペプラン\n\n※3名x4組は4名x3組に変更します。\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●+4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,160円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 12,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276469/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276469&stock_id=&date=20160205&s_pd=280132;5276469"
              }
            }
          },
          {
            "plan": {
              "planId": 5276480,
              "planName": "[早割]【8・9時台】3組～☆朝+各茶店1D+昼+特典付",
              "planType": 2,
              "limitedTimeFlag": 1,
              "price": 7550,
              "basePrice": 6482,
              "salesTax": 518,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 1,
              "addFee3b": 540,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 3,
              "compePlayMemberMin": 9,
              "compePrivilegeFree": "※コンペ特典としてボール1ダース付♪\n※5組以上ならさらに選べる賞品プレゼント♪（2,500円相当の季節のフルーツ詰合せor豚しゃぶ肉）\n●朝食バイキング・各茶店1ドリンク・昼食付♪ (昼食は1,300円を超える場合、差額を頂戴します。)\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": null,
              "other": "☆[早割]期間限定☆ \n\n☆予約期間中にご予約をされると･･･ \n\n特別限定価格で大変お得に♪ \n\n☆今がチャンス！是非ご予約を！！ \n\n※上記掲載プランの予約受付期間以降のご予約、プレー日等の変更は特典無効になりますので予めご了承下さい。 \n\n★皆様のご来場お待ちしております♪ \n\n\n【8・9時台限定】平日コンペプラン\n\n※3名x4組は4名x3組に変更します。\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●+4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,160円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 40,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276480/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276480&stock_id=&date=20160205&s_pd=280132;5276480"
              }
            }
          },
          {
            "plan": {
              "planId": 5276701,
              "planName": "【7・10時台限定】平日☆朝食+各茶店1D+昼食付♪",
              "planType": 1,
              "limitedTimeFlag": 0,
              "price": 7650,
              "basePrice": 6575,
              "salesTax": 525,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "【7・10時台限定】平日ベーシックプラン\n\n●朝食バイキング・各茶店1ドリンク・昼食付♪（昼食は1,300円を超える場合、差額を頂戴します。）\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●+4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,160円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 1,
                "stockCount": 12,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276701/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276701&stock_id=&date=20160205&s_pd=280132;5276701"
              }
            }
          },
          {
            "plan": {
              "planId": 5276703,
              "planName": "【8・9時台限定】平日☆朝食+各茶店1D+昼食付♪",
              "planType": 1,
              "limitedTimeFlag": 0,
              "price": 7950,
              "basePrice": 6852,
              "salesTax": 548,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "【8・9時台限定】平日ベーシックプラン\n\n●朝食バイキング・各茶店1ドリンク・昼食付♪（昼食は1,300円を超える場合、差額を頂戴します。）\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●+4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,160円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 1,
                "stockCount": 40,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276703/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276703&stock_id=&date=20160205&s_pd=280132;5276703"
              }
            }
          },
          {
            "plan": {
              "planId": 5276541,
              "planName": "[早割]【7・10時台】3組～☆朝昼会食+各茶店1D+特典付",
              "planType": 2,
              "limitedTimeFlag": 1,
              "price": 8150,
              "basePrice": 7038,
              "salesTax": 562,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 1,
              "addFee3b": 540,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 3,
              "compePlayMemberMin": 9,
              "compePrivilegeFree": "■会食付（1,080円相当の軽食+1SD）\n※コンペ特典としてボール2ダース付♪\n※5組以上ならさらに選べる賞品プレゼント♪（4,000円相当の季節のフルーツ詰合せor但馬牛肉）\n●朝食バイキング・各茶店1ドリンク・昼食付♪ (昼食は1,300円を超える場合、差額を頂戴します。)\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": null,
              "other": "☆[早割]期間限定☆ \n\n☆予約期間中にご予約をされると･･･ \n\n特別限定価格で大変お得に♪ \n\n☆今がチャンス！是非ご予約を！！ \n\n※上記掲載プランの予約受付期間以降のご予約、プレー日等の変更は特典無効になりますので予めご了承下さい。 \n\n★皆様のご来場お待ちしております♪ \n\n\n【7・10時台限定】平日コンペプラン（会食付）\n\n※3名x4組は4名x3組に変更します。\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●+4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,160円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 12,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276541/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276541&stock_id=&date=20160205&s_pd=280132;5276541"
              }
            }
          },
          {
            "plan": {
              "planId": 5276571,
              "planName": "[早割]【8・9時台】3組～☆朝昼会食+各茶店1D+特典付",
              "planType": 2,
              "limitedTimeFlag": 1,
              "price": 8450,
              "basePrice": 7315,
              "salesTax": 585,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 1,
              "addFee3b": 540,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 1,
              "compePlayGroupMin": 3,
              "compePlayMemberMin": 9,
              "compePrivilegeFree": "■会食付（1,080円相当の軽食+1SD）\n※コンペ特典としてボール2ダース付♪\n※5組以上ならさらに選べる賞品プレゼント♪（4,000円相当の季節のフルーツ詰合せor但馬牛肉）\n●朝食バイキング・各茶店1ドリンク・昼食付♪ (昼食は1,300円を超える場合、差額を頂戴します。)\n※特典付プランの場合、特典の内容はお一人様の料金に含まれます。",
              "compeOption": null,
              "other": "☆[早割]期間限定☆ \n\n☆予約期間中にご予約をされると･･･ \n\n特別限定価格で大変お得に♪ \n\n☆今がチャンス！是非ご予約を！！ \n\n※上記掲載プランの予約受付期間以降のご予約、プレー日等の変更は特典無効になりますので予めご了承下さい。 \n\n★皆様のご来場お待ちしております♪ \n\n\n【8・9時台限定】平日コンペプラン（会食付）\n\n※3名x4組は4名x3組に変更します。\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●+4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,160円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 40,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276571/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276571&stock_id=&date=20160205&s_pd=280132;5276571"
              }
            }
          },
          {
            "plan": {
              "planId": 5276103,
              "planName": "さば寿司お土産付プラン☆朝食+各茶店1D+昼食付♪",
              "planType": 2,
              "limitedTimeFlag": 0,
              "price": 8650,
              "basePrice": 7500,
              "salesTax": 600,
              "courseUseTax": 500,
              "otherTax": 50,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "■さば寿司(お土産)付プラン♪\n※肉厚･高品質の鯖を厳選･調理した自家製『さばの棒寿司』をお1人1本お土産に！\n※鯖の入荷状況により万が一準備できない場合には、同等の他の商品に変更させて頂く場合がありますので、予めご了承下さい。\n※『さばの棒寿司』は、1,620円でご購入いただくこともできます。\n\n●朝食バイキング・各茶店1ドリンク・昼食付♪\n（昼食は1,300円を超える場合、差額を頂戴します。）\n\n●1R乗用カートセルフプレー料金\n●朝食バイキング(無料)をご用意しておりますので、時間に余裕をもってご来場下さい。\n●各茶店で1ドリンクサービスとなっております。\n●ご来場時にはブレザー等の上着をご着用下さい。(6～9月は除く)\n●ハーフ2時間15分を目安にプレー進行にご協力下さい。\n●1組のHDCP合計が120を超えないように組合せして下さい。\n●各種優待券はご利用いただけませんので、予めご了承下さい。\n\n●＋4,320円(4Bの場合)でキャディ付に変更可能です。\n\n※平日は3日前からお1人様2,000円のキャンセル料を頂戴します。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 52,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/280132/plan_id/5276103/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=280132&plan_id=5276103&stock_id=&date=20160205&s_pd=280132;5276103"
              }
            }
          }
        ]
      }
    },
    {
      "Item": {
        "golfCourseId": 80111,
        "golfCourseName": "水戸・ゴルフ・クラブ",
        "golfCourseCaption": "日本プロゴルフマッチプレー選手権開催コースとして有名な水戸・ゴルフ・クラブは全体がみごとな赤松や杉林でおおわれ各ホールは完全にセパレートされています。\nゆったりと自然を生かした贅沢なレイアウト、全体的に雄大かつ躍動感に満ちたダイナミックなチャンピオンコースでお楽しみ下さい。",
        "golfCourseRsvType": 1,
        "areaCode": 8,
        "prefecture": "茨城県",
        "highwayCode": 11131,
        "highway": "常磐自動車道",
        "ic": "水戸",
        "icDistance": "5km以内",
        "golfCourseImageUrl": "http://booking.gora.golf.rakuten.co.jp/img/golf/80111/photo1.jpg",
        "displayWeekdayMinPrice": "平日 3,180円（2690円＋税）～",
        "displayWeekdayMinBasePrice": "平日 2,690円（総額 3,180円）～",
        "displayHolidayMinPrice": null,
        "displayHolidayMinBasePrice": null,
        "cancelFeeFlag": 0,
        "cancelFee": "",
        "ratingNum": 6897,
        "evaluation": 3.9,
        "reserveCalUrlPC": "http://search.gora.golf.rakuten.co.jp/cal/disp/c_id/80111/",
        "reserveCalUrlMobile": "http://gr.g.rakuten.co.jp/b/?menu=mbl_cal&act=disp&c_id=80111",
        "ratingUrlPC": "http://booking.gora.golf.rakuten.co.jp/voice/detail/c_id/80111",
        "ratingUrlMobile": "http://gr.g.rakuten.co.jp/b/?menu=mbl_voice&act=detail&c_id=80111",
        "planInfo": [
          {
            "plan": {
              "planId": 5256542,
              "planName": "平日薄暮ﾊｰﾌプレープラン！",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 3180,
              "basePrice": 2690,
              "salesTax": 215,
              "courseUseTax": 275,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 0,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "●~:*:●薄暮ﾊｰﾌプレープラン●~:*:●\n\n時間が出来たら気軽にゴルフ！！\n14時以降の9ホールﾊｰﾌプレープラン！\n\n※※必ず下記をお読みください※※\n\n・当日の状況によりコースが異なったりスタートが前後する事が\nございます。予めご了承ください。\n・チックイン時に精算となりますのでご注意下さい。\n・ロッカー・貴重品ロッカーのご使用は出来ませんのでご了承下さい。\n・2サム・３サム保障致します。割増料金もかかりません。\n・当日の進行状況等により日没になる可能性もございますのでご了承下さい。日没になった場合でもご返金等は出来ません。\n・キャディバックはお客様自身でマスター室までお運び下さい。また、カートへのキャディバックの積込み・プレー後の積み下ろし等もお客様自身でお願い致します。（完全セルフ方式となっております。）\n・練習場の利用は出来ませんので、ご了承ください。\n・コース売店の御利用は出来ません。\n・プレー前の食堂の御利用は可能ですが、現金払いのみとなります。（プレー後の利用は不可）\n・プレー後に浴室のご利用は出来ません。（シャワーの利用も不可。）",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 4,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/80111/plan_id/5256542/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=80111&plan_id=5256542&stock_id=&date=20160205&s_pd=80111;5256542"
              }
            }
          },
          {
            "plan": {
              "planId": 5350779,
              "planName": "【平日限定】11時台午後ｽﾙｰプラン！",
              "planType": 2,
              "limitedTimeFlag": 0,
              "price": 4400,
              "basePrice": 3565,
              "salesTax": 285,
              "courseUseTax": 550,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 0,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "●~:*:●午後スループレープラン●~:*:●\n\n時間が出来たら気軽にゴルフ！！\n11時30分～の1ラウンドｽﾙｰプレープラン！\n\n※※必ず下記をお読みください※※\n\n・スタート時間が前後いたしますので11時00分までにチェックイン及び精算を完了頂きますようお願い致します。\n・当日の状況によりコースが異なったりスタートが前後する事が\nございます。予めご了承ください。\n・チェックイン時に精算となりますのでご注意下さい。\n・浴室・ロッカー・貴重品ロッカーのご使用は出来ませんのでご了承下さい。\n・2サム・３サム保障致します。割増料金もかかりません。\n・当日の進行状況等により日没になる可能性もございますのでご了承下さい。日没になった場合でもご返金等は出来ません。\n・キャディバックはお客様自身でマスター室までお運び下さい。また、カートへのキャディバックの積込み・プレー後の積み下ろし等もお客様自身でお願い致します。（完全セルフ方式となっております。）\n・練習場の利用は出来ませんので、ご了承ください。\n・コース売店の御利用は出来ません。\n・プレー前の食堂の御利用は可能ですが、現金払いのみとなります。（プレー後の利用は不可）",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 3,
                "stockCount": 8,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/80111/plan_id/5350779/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=80111&plan_id=5350779&stock_id=&date=20160205&s_pd=80111;5350779"
              }
            }
          },
          {
            "plan": {
              "planId": 5256549,
              "planName": "2月平日レギュラープラン5600円！【昼食付】",
              "planType": 3,
              "limitedTimeFlag": 0,
              "price": 5600,
              "basePrice": 4676,
              "salesTax": 374,
              "courseUseTax": 550,
              "otherTax": 0,
              "playerNumMin": 2,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 1,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 0,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0,
              "lesson": 0,
              "openCompe": 0,
              "regularCompe": 0,
              "compePlayGroupMin": 0,
              "compePlayMemberMin": 0,
              "compePrivilegeFree": null,
              "compeOption": null,
              "other": "★━━━━━★　平日ゲスト様プラン♪　★━━━━━★ \n\n・平日は昼食付となります。1240円（税別）を超えるメニューにつきまては差額が発生いたします。\n・ロッカーご使用の場合には別途313円（税込）がかかります。\n・2サム・３サムプレーは保障致します。割増料金もございません。\n・セルフプレー・全組乗用カート付。\n但し2名プレーの際は2人用カートになる場合がございますのでご了承くださいませ。\nなお、キャディ付きは廃止となっております。ご了承下さい。\n・割引券や他の優待券との併用不可\n・練習場利用はオープンからAM10：30までとなります。\n・御予約頂きましたプレー30分前までにチェックインをして頂きますようご協力お願い致します。30分前のチェックインに間に合わない場合にはスタート時間が大幅に変更となる可能性がございますので、ご了承下さい。",
              "pointFlag": 0,
              "point": 0,
              "callInfo": {
                "playDate": "2016-02-05",
                "stockStatus": 4,
                "stockCount": 77,
                "reservePageUrlPC": "https://booking.gora.golf.rakuten.co.jp/rsv/slcttime/c_id/80111/plan_id/5256549/date/20160205",
                "reservePageUrlMobile": "https://gr.g.rakuten.co.jp/b/?menu=mbl_rsv&act=slcttime&c_id=80111&plan_id=5256549&stock_id=&date=20160205&s_pd=80111;5256549"
              }
            }
          },
          {
            "plan": {
              "planId": 5256556,
              "planName": "お得なパーティ付プラン★セルフ昼食付★3組10名以上",
              "planType": 2,
              "limitedTimeFlag": 0,
              "price": 6200,
              "basePrice": 5232,
              "salesTax": 418,
              "courseUseTax": 550,
              "otherTax": 0,
              "playerNumMin": 3,
              "playerNumMax": 4,
              "startTimeZone": "",
              "round": "1R",
              "caddie": 0,
              "cart": 2,
              "assu2sum": 0,
              "addFee2bFlag": 0,
              "addFee2b": 0,
              "assortment2bFlag": 1,
              "addFee3bFlag": 0,
              "addFee3b": 0,
              "assortment3bFlag": 0,
              "discount4sumFlag": 0,
              "lunch": 1,
              "drink": 0,
              "stay": 0
```


## Rakuten Recipe

![Rakuten Recipe](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten-recipes.png)
* **Name** Rakuten Recipe
* **URL** http://recipe.rakuten.co.jp/
* **Description** Rakuten Recipe is a community for sharing cooking recipes.

### Recipe/CategoryRanking

#### Description

Gets the top 4 ranked recipes.
#### Resource URL

https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20121121
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
categoryType<br>*Category Type* | string | Optional | Category type.<br>("all" is used when not specified)
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20121121?applicationId=REPLACE_WITH_YOUR_APP_ID
##### Response

```json
{
  "result": [
    {
      "recipeId": 1050000502,
      "recipeTitle": "今まで食べた大根の漬物の中で一番美味しい大根の漬物",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1050000502/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/bc0564cd6b10ee11fa5e96f5091e709b42a3aa1b.94.1.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/bc0564cd6b10ee11fa5e96f5091e709b42a3aa1b.94.1.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/bc0564cd6b10ee11fa5e96f5091e709b42a3aa1b.94.1.3.2.jpg?thum=55",
      "pickup": 0,
      "shop": 0,
      "nickname": "ｙｂｋｍｋ★",
      "recipeDescription": "簡単ですがとっても美味しいんです！！\n\n刻んでおにぎりの具材にしても◎",
      "recipeMaterial": [
        "大根",
        "★砂糖",
        "★しょうゆ",
        "★酢",
        "★昆布"
      ],
      "recipeIndication": "約30分",
      "recipeCost": "300円前後",
      "recipePublishday": "2010/12/20 23:32:19",
      "rank": "1"
    },
    {
      "recipeId": 1140021340,
      "recipeTitle": "つなぎはマヨで簡単！　蓮根はさみ照り焼き",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1140021340/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/a6a50d94d735f9dad01c9233008fb6bd587a8642.65.2.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/a6a50d94d735f9dad01c9233008fb6bd587a8642.65.2.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/a6a50d94d735f9dad01c9233008fb6bd587a8642.65.2.3.2.jpg?thum=55",
      "pickup": 1,
      "shop": 0,
      "nickname": "Slice of Coffee",
      "recipeDescription": "一人前100円以下の　胸肉、ささ身を使った蓮根はさみ照り焼きです。\nつなぎはマヨネーズなので簡単に作れます。",
      "recipeMaterial": [
        "ささ身　3本　or　胸肉(ミンチ)",
        "細ねぎ",
        "蓮根　太め",
        "塩、胡椒",
        "マヨネーズ",
        "小麦粉",
        "☆醤油",
        "☆みりん",
        "☆酒"
      ],
      "recipeIndication": "約15分",
      "recipeCost": "100円以下",
      "recipePublishday": "2014/12/22 15:21:51",
      "rank": "2"
    },
    {
      "recipeId": 1510010130,
      "recipeTitle": "HMとハチミツで簡単おいしい！炊飯器ケーキ",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1510010130/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/f8bc74536866846c7cbfae5d9a25c500a9b12cd4.43.2.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/f8bc74536866846c7cbfae5d9a25c500a9b12cd4.43.2.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/f8bc74536866846c7cbfae5d9a25c500a9b12cd4.43.2.3.2.jpg?thum=55",
      "pickup": 1,
      "shop": 0,
      "nickname": "hapihapi.jp",
      "recipeDescription": "ホットケーキミックスとハチミツでしっとりおいしいケーキか簡単に作れます。\n火加減は炊飯器にオマカセです。",
      "recipeMaterial": [
        "ホットケーキミックス",
        "ハチミツ",
        "卵",
        "塩",
        "牛乳"
      ],
      "recipeIndication": "指定なし",
      "recipeCost": "指定なし",
      "recipePublishday": "2014/05/12 17:00:45",
      "rank": "3"
    },
    {
      "recipeId": 1960000322,
      "recipeTitle": "簡単！激旨！合わせて置くだけの大根漬物",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1960000322/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/2063225afffe7c73bb1662a0220efe1a4ddacf15.48.2.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/2063225afffe7c73bb1662a0220efe1a4ddacf15.48.2.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/2063225afffe7c73bb1662a0220efe1a4ddacf15.48.2.3.2.jpg?thum=55",
      "pickup": 1,
      "shop": 0,
      "nickname": "POPOTANKOBU",
      "recipeDescription": "他の料理サイトで1000件レポを頂いている自慢のお漬物です\n大根・人参‥パクパクと手が止まりません！\n食べた人が「美味しい～！」と、必ずレシピを聞いてくれます★",
      "recipeMaterial": [
        "大根",
        "◆酢",
        "◆塩",
        "◆砂糖",
        "*砂糖はお好みで調節して下さい♪",
        "◆酒",
        "お好みで（漬物昆布・ゆず皮・鷹の爪）",
        "一緒に人参・胡瓜・セロリ等漬けてもOK"
      ],
      "recipeIndication": "5分以内",
      "recipeCost": "300円前後",
      "recipePublishday": "2010/12/31 01:10:38",
      "rank": "4"
    }
  ]
}
```


### Recipe/CategoryList

#### Description

Gets the full recipe category list.
#### Resource URL

https://app.rakuten.co.jp/services/api/Recipe/CategoryList/20121121
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
categoryId<br>*Category ID* | string | Optional | Example:<br><code>categoryId=10</code> (large category)<br><code>categoryId=10-276</code> (medium category)<br><code>categoryId=10-276-824</code> (small category)<br>If you want to specify a medium or small category, please join the parent categories using hyphens.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Recipe/CategoryList/20121121?applicationId=REPLACE_WITH_YOUR_APP_ID
##### Response

```json
{
  "result": {
    "large": [
      {
        "categoryId": "30",
        "categoryName": "人気メニュー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30/"
      },
      {
        "categoryId": "31",
        "categoryName": "定番の肉料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31/"
      },
      {
        "categoryId": "32",
        "categoryName": "定番の魚料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32/"
      },
      {
        "categoryId": "33",
        "categoryName": "卵料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/33/"
      },
      {
        "categoryId": "14",
        "categoryName": "ご飯もの",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14/"
      },
      {
        "categoryId": "15",
        "categoryName": "パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15/"
      },
      {
        "categoryId": "16",
        "categoryName": "麺・粉物料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16/"
      },
      {
        "categoryId": "17",
        "categoryName": "汁物・スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17/"
      },
      {
        "categoryId": "23",
        "categoryName": "鍋料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23/"
      },
      {
        "categoryId": "18",
        "categoryName": "サラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18/"
      },
      {
        "categoryId": "22",
        "categoryName": "パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22/"
      },
      {
        "categoryId": "21",
        "categoryName": "お菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21/"
      },
      {
        "categoryId": "10",
        "categoryName": "肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10/"
      },
      {
        "categoryId": "11",
        "categoryName": "魚",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11/"
      },
      {
        "categoryId": "12",
        "categoryName": "野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12/"
      },
      {
        "categoryId": "34",
        "categoryName": "果物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/34/"
      },
      {
        "categoryId": "19",
        "categoryName": "ソース・調味料・ドレッシング",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19/"
      },
      {
        "categoryId": "27",
        "categoryName": "飲みもの",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27/"
      },
      {
        "categoryId": "35",
        "categoryName": "大豆・豆腐",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/35/"
      },
      {
        "categoryId": "13",
        "categoryName": "その他の食材",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13/"
      },
      {
        "categoryId": "20",
        "categoryName": "お弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20/"
      },
      {
        "categoryId": "36",
        "categoryName": "簡単料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/36/"
      },
      {
        "categoryId": "37",
        "categoryName": "節約料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/37/"
      },
      {
        "categoryId": "38",
        "categoryName": "今日の献立",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/38/"
      },
      {
        "categoryId": "39",
        "categoryName": "健康料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/39/"
      },
      {
        "categoryId": "40",
        "categoryName": "調理器具",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/40/"
      },
      {
        "categoryId": "26",
        "categoryName": "その他の目的・シーン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26/"
      },
      {
        "categoryId": "41",
        "categoryName": "中華料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/41/"
      },
      {
        "categoryId": "42",
        "categoryName": "韓国料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/42/"
      },
      {
        "categoryId": "43",
        "categoryName": "イタリア料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/43/"
      },
      {
        "categoryId": "44",
        "categoryName": "フランス料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/44/"
      },
      {
        "categoryId": "25",
        "categoryName": "西洋料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25/"
      },
      {
        "categoryId": "46",
        "categoryName": "エスニック料理・中南米",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/46/"
      },
      {
        "categoryId": "47",
        "categoryName": "沖縄料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/47/"
      },
      {
        "categoryId": "48",
        "categoryName": "日本各地の郷土料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/48/"
      },
      {
        "categoryId": "24",
        "categoryName": "行事・イベント",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24/"
      },
      {
        "categoryId": "49",
        "categoryName": "おせち料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/49/"
      },
      {
        "categoryId": "50",
        "categoryName": "クリスマス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/50/"
      },
      {
        "categoryId": "51",
        "categoryName": "ひな祭り",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/51/"
      },
      {
        "categoryId": "52",
        "categoryName": "春（3月～5月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/52/"
      },
      {
        "categoryId": "53",
        "categoryName": "夏（6月～8月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/53/"
      },
      {
        "categoryId": "54",
        "categoryName": "秋（9月～11月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/54/"
      },
      {
        "categoryId": "55",
        "categoryName": "冬（12月～2月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/55/"
      }
    ],
    "medium": [
      {
        "categoryId": 275,
        "categoryName": "牛肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-275/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 276,
        "categoryName": "豚肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-276/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 277,
        "categoryName": "鶏肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-277/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 278,
        "categoryName": "ひき肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-278/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 68,
        "categoryName": "ベーコン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-68/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 66,
        "categoryName": "ソーセージ・ウインナー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-66/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 67,
        "categoryName": "ハム",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-67/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 69,
        "categoryName": "その他のお肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-69/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 70,
        "categoryName": "サーモン・鮭",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-70/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 71,
        "categoryName": "いわし",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-71/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 72,
        "categoryName": "さば",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-72/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 73,
        "categoryName": "あじ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-73/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 74,
        "categoryName": "ぶり",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-74/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 75,
        "categoryName": "さんま",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-75/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 76,
        "categoryName": "鯛",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-76/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 77,
        "categoryName": "マグロ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-77/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 443,
        "categoryName": "たら",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-443/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 78,
        "categoryName": "その他のさかな",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-78/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 80,
        "categoryName": "いか",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-80/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 81,
        "categoryName": "たこ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-81/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 79,
        "categoryName": "エビ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-79/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 83,
        "categoryName": "かに",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-83/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 444,
        "categoryName": "牡蠣",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-444/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 82,
        "categoryName": "貝類",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-82/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 445,
        "categoryName": "明太子・魚卵",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-445/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 446,
        "categoryName": "その他の魚介",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-446/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 447,
        "categoryName": "なす",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-447/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 448,
        "categoryName": "かぼちゃ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-448/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 449,
        "categoryName": "大根",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-449/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 450,
        "categoryName": "きゅうり",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-450/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 97,
        "categoryName": "じゃがいも",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-97/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 452,
        "categoryName": "さつまいも",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-452/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 98,
        "categoryName": "キャベツ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-98/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 453,
        "categoryName": "白菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-453/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 454,
        "categoryName": "トマト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-454/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 99,
        "categoryName": "もやし",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-99/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 456,
        "categoryName": "小松菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-456/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 457,
        "categoryName": "ほうれん草",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-457/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 455,
        "categoryName": "ごぼう",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-455/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 451,
        "categoryName": "アボカド",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-451/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 96,
        "categoryName": "玉ねぎ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-96/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 458,
        "categoryName": "ブロッコリー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-458/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 95,
        "categoryName": "にんじん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-95/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 100,
        "categoryName": "春野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-100/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 101,
        "categoryName": "夏野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-101/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 102,
        "categoryName": "秋野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-102/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 103,
        "categoryName": "冬野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-103/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 105,
        "categoryName": "きのこ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-105/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 107,
        "categoryName": "香味野菜・ハーブ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-107/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 104,
        "categoryName": "その他の野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-104/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 478,
        "categoryName": "もち米",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-478/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 479,
        "categoryName": "マカロニ・ペンネ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-479/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 480,
        "categoryName": "ホットケーキミックス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-480/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 481,
        "categoryName": "粉類",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-481/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 108,
        "categoryName": "練物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-108/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 109,
        "categoryName": "加工食品",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-109/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 482,
        "categoryName": "チーズ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-482/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 483,
        "categoryName": "ヨーグルト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-483/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 111,
        "categoryName": "こんにゃく",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-111/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 112,
        "categoryName": "しらたき",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-112/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 113,
        "categoryName": "海藻",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-113/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 114,
        "categoryName": "乾物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-114/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 484,
        "categoryName": "漬物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-484/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 115,
        "categoryName": "その他の食材",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-115/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 121,
        "categoryName": "オムライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-121/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 131,
        "categoryName": "チャーハン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-131/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 126,
        "categoryName": "パエリア",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-126/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 124,
        "categoryName": "タコライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-124/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 122,
        "categoryName": "チキンライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-122/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 123,
        "categoryName": "ハヤシライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-123/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 125,
        "categoryName": "ロコモコ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-125/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 127,
        "categoryName": "ピラフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-127/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 368,
        "categoryName": "ハッシュドビーフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-368/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 128,
        "categoryName": "その他○○ライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-128/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 129,
        "categoryName": "寿司",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-129/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 130,
        "categoryName": "丼物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-130/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 132,
        "categoryName": "炊き込みご飯",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-132/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 133,
        "categoryName": "おかゆ・雑炊類",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-133/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 134,
        "categoryName": "おにぎり",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-134/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 135,
        "categoryName": "アレンジごはん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-135/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 271,
        "categoryName": "その他のごはん料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-271/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 687,
        "categoryName": "カルボナーラ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-687/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 137,
        "categoryName": "ミートソース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-137/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 676,
        "categoryName": "ナポリタン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-676/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 681,
        "categoryName": "ペペロンチーノ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-681/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 369,
        "categoryName": "ジェノベーゼ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-369/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 677,
        "categoryName": "ペスカトーレ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-677/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 683,
        "categoryName": "たらこパスタ・明太子パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-683/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 682,
        "categoryName": "ボンゴレ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-682/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 678,
        "categoryName": "アラビアータ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-678/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 679,
        "categoryName": "トマトクリームパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-679/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 684,
        "categoryName": "納豆パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-684/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 680,
        "categoryName": "トマト系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-680/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 138,
        "categoryName": "クリーム系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-138/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 139,
        "categoryName": "オイル・塩系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-139/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 140,
        "categoryName": "チーズ系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-140/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 141,
        "categoryName": "バジルソース系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-141/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 142,
        "categoryName": "和風パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-142/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 685,
        "categoryName": "きのこパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-685/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 686,
        "categoryName": "ツナパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-686/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 143,
        "categoryName": "冷製パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-143/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 145,
        "categoryName": "スープスパ・スープパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-145/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 146,
        "categoryName": "その他のパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-146/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 144,
        "categoryName": "パスタソース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-144/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 147,
        "categoryName": "ニョッキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-147/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 151,
        "categoryName": "ラザニア",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-151/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 382,
        "categoryName": "ラビオリ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-382/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 152,
        "categoryName": "うどん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-152/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 153,
        "categoryName": "蕎麦",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-153/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 154,
        "categoryName": "そうめん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-154/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 155,
        "categoryName": "焼きそば",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-155/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 156,
        "categoryName": "ラーメン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-156/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 383,
        "categoryName": "冷やし中華",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-383/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 384,
        "categoryName": "つけ麺",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-384/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 272,
        "categoryName": "その他の麺",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-272/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 385,
        "categoryName": "お好み焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-385/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 386,
        "categoryName": "たこ焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-386/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 158,
        "categoryName": "粉物料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-158/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 159,
        "categoryName": "味噌汁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-159/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 161,
        "categoryName": "豚汁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-161/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 387,
        "categoryName": "けんちん汁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-387/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 160,
        "categoryName": "お吸い物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-160/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 388,
        "categoryName": "かぼちゃスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-388/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 169,
        "categoryName": "野菜スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-169/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 389,
        "categoryName": "チャウダー・クラムチャウダー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-389/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 171,
        "categoryName": "コーンスープ・ポタージュ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-171/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 168,
        "categoryName": "トマトスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-168/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 167,
        "categoryName": "コンソメスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-167/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 170,
        "categoryName": "クリームスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-170/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 164,
        "categoryName": "中華スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-164/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 165,
        "categoryName": "和風スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-165/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 166,
        "categoryName": "韓国風スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-166/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 173,
        "categoryName": "その他のスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-173/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 390,
        "categoryName": "ポトフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-390/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 162,
        "categoryName": "その他の汁物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-162/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 415,
        "categoryName": "ポテトサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-415/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 416,
        "categoryName": "春雨サラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-416/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 417,
        "categoryName": "大根サラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-417/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 418,
        "categoryName": "コールスロー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-418/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 419,
        "categoryName": "かぼちゃサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-419/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 420,
        "categoryName": "ごぼうサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-420/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 421,
        "categoryName": "マカロニサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-421/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 187,
        "categoryName": "シーザーサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-187/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 423,
        "categoryName": "コブサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-423/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 424,
        "categoryName": "タラモサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-424/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 189,
        "categoryName": "スパゲティサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-189/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 190,
        "categoryName": "ホットサラダ・温野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-190/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 703,
        "categoryName": "ジャーサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-703/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 184,
        "categoryName": "素材で選ぶサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-184/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 188,
        "categoryName": "味付けで選ぶサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-188/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 185,
        "categoryName": "マヨネーズを使ったサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-185/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 186,
        "categoryName": "ナンプラーを使ったサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-186/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 191,
        "categoryName": "その他のサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-191/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 192,
        "categoryName": "ソース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-192/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 193,
        "categoryName": "タレ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-193/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 194,
        "categoryName": "つゆ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-194/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 195,
        "categoryName": "だし",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-195/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 196,
        "categoryName": "ドレッシング",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-196/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 675,
        "categoryName": "発酵食品・発酵調味料",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-675/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 273,
        "categoryName": "その他調味料",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-273/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 274,
        "categoryName": "スパイス＆ハーブ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-274/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 463,
        "categoryName": "柚子胡椒",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-463/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 464,
        "categoryName": "オリーブオイル",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-464/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 700,
        "categoryName": "ココナッツオイル",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-700/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 485,
        "categoryName": "キャラ弁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-485/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 197,
        "categoryName": "お弁当のおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-197/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 486,
        "categoryName": "運動会のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-486/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 487,
        "categoryName": "お花見のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-487/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 488,
        "categoryName": "遠足・ピクニックのお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-488/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 198,
        "categoryName": "色別おかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-198/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 199,
        "categoryName": "作り置き・冷凍できるおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-199/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 200,
        "categoryName": "すきまおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-200/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 201,
        "categoryName": "使い回しおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-201/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 202,
        "categoryName": "子供のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-202/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 203,
        "categoryName": "大人のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-203/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 258,
        "categoryName": "部活のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-258/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 204,
        "categoryName": "クッキー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-204/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 440,
        "categoryName": "スイートポテト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-440/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 205,
        "categoryName": "チーズケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-205/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 438,
        "categoryName": "シフォンケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-438/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 439,
        "categoryName": "パウンドケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-439/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 206,
        "categoryName": "ケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-206/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 215,
        "categoryName": "ホットケーキ・パンケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-215/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 207,
        "categoryName": "タルト・パイ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-207/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 208,
        "categoryName": "チョコレート",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-208/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 209,
        "categoryName": "スコーン・マフィン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-209/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 210,
        "categoryName": "焼き菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-210/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 211,
        "categoryName": "プリン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-211/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 216,
        "categoryName": "ドーナツ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-216/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 212,
        "categoryName": "シュークリーム・エクレア",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-212/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 441,
        "categoryName": "ゼリー・寒天・ムース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-441/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 442,
        "categoryName": "アイス・シャーベット",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-442/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 214,
        "categoryName": "和菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-214/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 217,
        "categoryName": "その他のお菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-217/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 218,
        "categoryName": "クリーム・ジャム",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-218/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 432,
        "categoryName": "サンドイッチ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-432/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 433,
        "categoryName": "フレンチトースト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-433/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 434,
        "categoryName": "食パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-434/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 435,
        "categoryName": "蒸しパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-435/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 436,
        "categoryName": "ホットサンド",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-436/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 229,
        "categoryName": "惣菜パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-229/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 221,
        "categoryName": "菓子パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-221/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 220,
        "categoryName": "プレーンなパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-220/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 222,
        "categoryName": "クロワッサン・デニッシュ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-222/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 219,
        "categoryName": "ハードブレッド",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-219/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 223,
        "categoryName": "天然酵母パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-223/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 227,
        "categoryName": "世界各国のパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-227/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 231,
        "categoryName": "ヘルシーなパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-231/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 437,
        "categoryName": "キャラパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-437/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 230,
        "categoryName": "その他のパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-230/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 391,
        "categoryName": "おでん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-391/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 392,
        "categoryName": "すき焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-392/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 393,
        "categoryName": "もつ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-393/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 394,
        "categoryName": "しゃぶしゃぶ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-394/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 395,
        "categoryName": "キムチ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-395/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 396,
        "categoryName": "湯豆腐",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-396/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 397,
        "categoryName": "豆乳鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-397/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 398,
        "categoryName": "ちゃんこ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-398/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 399,
        "categoryName": "寄せ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-399/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 400,
        "categoryName": "水炊き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-400/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 401,
        "categoryName": "トマト鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-401/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 402,
        "categoryName": "あんこう鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-402/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 403,
        "categoryName": "石狩鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-403/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 404,
        "categoryName": "カレー鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-404/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 405,
        "categoryName": "きりたんぽ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-405/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 406,
        "categoryName": "韓国鍋・チゲ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-406/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 407,
        "categoryName": "雪見鍋（みぞれ鍋）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-407/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 408,
        "categoryName": "蒸し鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-408/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 409,
        "categoryName": "ねぎま鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-409/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 410,
        "categoryName": "鴨鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-410/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 411,
        "categoryName": "カニ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-411/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 412,
        "categoryName": "火鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-412/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 413,
        "categoryName": "牡蠣鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-413/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 698,
        "categoryName": "白味噌鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-698/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 234,
        "categoryName": "その他の鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-234/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 631,
        "categoryName": "お食い初め料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-631/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 632,
        "categoryName": "誕生日の料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-632/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 633,
        "categoryName": "結婚記念日",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-633/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 634,
        "categoryName": "パーティー料理・ホームパーティ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-634/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 635,
        "categoryName": "子どものパーティ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-635/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 238,
        "categoryName": "バーベキュー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-238/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 244,
        "categoryName": "その他イベント",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-244/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 256,
        "categoryName": "スペイン料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-256/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 701,
        "categoryName": "イギリス料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-701/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 248,
        "categoryName": "ロシア料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-248/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 255,
        "categoryName": "ドイツ料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-255/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 257,
        "categoryName": "トルコ料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-257/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 262,
        "categoryName": "おもてなし料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-262/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 260,
        "categoryName": "おつまみ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-260/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 261,
        "categoryName": "限られた食材・調理器具で工夫",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-261/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 265,
        "categoryName": "料理のちょいテク・裏技",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-265/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 266,
        "categoryName": "コーヒー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-266/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 267,
        "categoryName": "お茶",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-267/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 268,
        "categoryName": "ソフトドリンク",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-268/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 465,
        "categoryName": "ジュース・スムージー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-465/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 269,
        "categoryName": "お酒",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-269/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 300,
        "categoryName": "ハンバーグ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-300/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 301,
        "categoryName": "餃子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-301/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 302,
        "categoryName": "肉じゃが",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-302/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 307,
        "categoryName": "カレー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-307/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 303,
        "categoryName": "牛丼",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-303/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 304,
        "categoryName": "親子丼",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-304/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 305,
        "categoryName": "豚の生姜焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-305/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 306,
        "categoryName": "グラタン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-306/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 309,
        "categoryName": "唐揚げ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-309/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 310,
        "categoryName": "コロッケ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-310/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 308,
        "categoryName": "シチュー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-308/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 311,
        "categoryName": "煮物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-311/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 312,
        "categoryName": "野菜炒め",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-312/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 313,
        "categoryName": "天ぷら",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-313/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 314,
        "categoryName": "揚げ物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-314/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 315,
        "categoryName": "豆腐料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-315/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 316,
        "categoryName": "和え物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-316/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 317,
        "categoryName": "酢の物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-317/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 318,
        "categoryName": "ローストビーフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-318/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 319,
        "categoryName": "豚の角煮",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-319/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 320,
        "categoryName": "チキン南蛮",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-320/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 321,
        "categoryName": "ピーマンの肉詰め",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-321/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 323,
        "categoryName": "ロールキャベツ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-323/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 324,
        "categoryName": "スペアリブ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-324/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 325,
        "categoryName": "ローストチキン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-325/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 326,
        "categoryName": "もつ煮込み",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-326/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 327,
        "categoryName": "ミートボール・肉団子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-327/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 328,
        "categoryName": "ミートローフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-328/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 329,
        "categoryName": "牛すじ煮込み",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-329/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 330,
        "categoryName": "とんかつ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-330/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 331,
        "categoryName": "ポークソテー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-331/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 332,
        "categoryName": "つくね",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-332/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 333,
        "categoryName": "チャーシュー（焼き豚）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-333/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 334,
        "categoryName": "煮豚",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-334/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 322,
        "categoryName": "ステーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-322/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 335,
        "categoryName": "鶏肉料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-335/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 336,
        "categoryName": "ぶり大根",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-336/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 337,
        "categoryName": "ぶりの照り焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-337/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 338,
        "categoryName": "さばの味噌煮",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-338/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 339,
        "categoryName": "煮魚",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-339/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 340,
        "categoryName": "あさりの酒蒸し",
        "c
```


## Other

![Other](https://media.antoniotajuelo.com/rakuten/service/logo/rakuten.png)
* **Name** Other
* **Description** Other APIs offered by Rakuten that do not belong to a specific service.

### HighComissionShop/List

#### Description

Gets up to 30 Rakuten Ichiba shops offering an affiliate commission of 1.1 or higher.
#### Resource URL

https://app.rakuten.co.jp/services/api/HighCommissionShop/List/20131205
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | ---
hits<br>*How many results to display on each page* | integer | Optional | Integer 1 to 30.
page<br>*Page number* | integer | Optional | Integer 1 or more.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/HighCommissionShop/List/20131205?applicationId=REPLACE_WITH_YOUR_APP_ID&hits=3
##### Response

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

