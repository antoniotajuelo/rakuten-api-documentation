
# IchibaItem/Search

## Description

Gets up to 30 items by keywords, shop, shop item code or genre.
## Resource URL

https://app.rakuten.co.jp/services/api/IchibaItem/Search/20140222
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
keyword<br>*Search keywords* | string | At least one is required | UTF-8 URL encoded string<br>The keyword parameter can have a maximum length of 128 single byte characters<br>The keyword parameter is delimited with single byte space characters. This defaults to an AND operation including all the keywords. To use OR instead set the orFlag to 1.<br>Each search keyword must be at least two single byte characters or one double byte character.<br>An exception is a minimum of two characters if the search keywords are using hiragana, katakana, or symbols.
shopCode<br>*Shop code* | string | At least one is required | The portion of the shop URL listed as <code>xyz</code>: <code>http://www.rakuten.co.jp/xyz</code>
itemCode<br>*Item code* | string | At least one is required | Included in the output parameters of the Item Search, Item Ranking, and Bookmark APIs. <br>Please set a value in the form of <code>shop:1234</code>. 
genreId<br>*Genre ID* | long | At least one is required | ID to specify a genre in Rakuten Ichiba<br>Please use the Rakuten Ichiba Genre Search API 2 to look up genre names and genre relations.<br>**Default Value:** <code>0</code>
tagId<br>*Tag ID* | long | Optional | Comma separated (maximum 10 IDs)<br>ID to specify a tag in Rakuten Ichiba.
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30<br>**Default Value:** <code>30</code>
page<br>*Result page* | integer | Optional | An integer between 1 and 100<br>**Default Value:** <code>1</code>
sort<br>*Sort* | string | Optional | UTF-8 URL encoding is required. <br>*Valid Values:*<br><code>+affiliateRate</code> Affiliate Rate (Ascending order)<br><code>-affiliateRate</code> Affiliate Rate (Descending order)<br><code>+reviewCount</code> Number of reviews (Ascending order)<br><code>-reviewCount</code> Number of reviews (Descending order)<br><code>+reviewAverage</code> Average review rating (Ascending order)<br><code>-reviewAverage</code> Average review rating (Descending order)<br><code>+itemPrice</code> Price (Ascending order)<br><code>-itemPrice</code> Price (Descending order)<br><code>+updateTimestamp</code> Time of item update (Ascending order)<br><code>-updateTimestamp</code> Time of item update (Descending order)<br><code>standard</code> Rakuten standard sort<br>**Default Value:** <code>standard</code>
minPrice<br>*Minimum price* | long | Optional | An integer greater than 0 and less than 999,999,999
maxPrice<br>*Maximum price* | long | Optional | An integer greater than 0 and less than 999,999,999<br><code>maxPrice</code> must be greater than <code>minPrice</code>.
availability<br>*Availability* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only available products<br>**Default Value:** <code>1</code>
field<br>*Search field* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Broad search (prefer more matches with the same keyword)<br><code>1</code> Restricted search (prefer fewer matches with the same keyword)<br>**Default Value:** <code>1</code>
carrier<br>*Platform* | integer | Optional | Choose the target platform for type of information to return: PC, mobile, or smartphone <br>*Valid Values:*<br><code>0</code> PC<br><code>1</code> mobile (*Japan only)<br><code>2</code> smartphone<br>**Default Value:** <code>0</code>
imageFlag<br>*Has image flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Search all products<br><code>1</code> Search only products with images<br>**Default Value:** <code>0</code>
orFlag<br>*OR search flag* | integer | Optional | Choose between AND searches and OR searches when there are multiple keywords. <br>*It isn't possible to use a complex search condition like "(A and B) or C".<br>*Valid Values:*<br><code>0</code> AND<br><code>1</code> OR<br>**Default Value:** <code>0</code>
NGKeyword<br>*Excluded keywords* | string | Optional | Words to exclude from search results<br>Strings encoded with UTF-8 URL encoding<br>Same format as keyword
purchaseType<br>*Purchase type* | integer | Optional | Narrow search by purchase type <br>*Valid Values:*<br><code>0</code> Normal purchase<br><code>1</code> Periodic purchase (a service that allows customers to buy goods they choose on a cycle they specify).<br><code>2</code> Distribution group purchase (a service that allows the shop to choose items and also choose the number of times they are delivered).<br>**Default Value:** <code>0</code>
shipOverseasFlag<br>*Overseas shipping flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products that can be shipped overseas<br>**Default Value:** <code>0</code>
shipOverseasArea<br>*Overseas shipping area* | string | Optional | It is possible to restrict searches based on delivery areas. <br>Check the overseas delivery area codes<br>*shipOverseasFlag must be 1<br>**Default Value:** <code>ALL</code>
asurakuFlag<br>*Asuraku flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only items that can use the Asuraku service<br>**Default Value:** <code>0</code>
asurakuArea<br>*Asuraku area* | integer | Optional | It is possible to restrict searches based on delivery areas.<br>Check the Asuraku delivery area codes<br>*asurakuFlag must be 1<br>**Default Value:** <code>0</code>
pointRateFlag<br>*Point multiplier flag* | integer | Optional | 0: All products<br>1: Only items with point multipliers<br>**Default Value:** <code>0</code>
pointRate<br>*Point multiplier* | integer | Optional | An integer from 2 to 10 (e.g. 5 means points will be multiplied by five) <br>*pointRateFlag must be 1
postageFlag<br>*Postage flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only items with postage included/free shipping<br>**Default Value:** <code>0</code>
creditCardFlag<br>*Credit card flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products purchaseable with credit cards<br>**Default Value:** <code>0</code>
giftFlag<br>*Giftwrap flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products with giftwrapping available<br>**Default Value:** <code>0</code>
hasReviewFlag<br>*Has review flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products with reviews<br>**Default Value:** <code>0</code>
maxAffiliateRate<br>*Maximum affiliate rate	* | float | Optional | A number from 1.0 to 99.9 (e.g. 5.0 for products with an affiliate rate up to 5%).<br>Don't show if the affiliate rate is higher than specified.<br>Up to one decimal place can be specified.
minAffiliateRate<br>*Minimum affiliate rate* | float | Optional | A number from 1.0 to 99.9 (e.g. 5.0 for products with an affiliate rate above 5%).<br>Don't show if the affiliate rate is lower than specified.<br>Up to one decimal place can be specified.<br>Specify an affiliate rate lower than the maximum rate.
hasMovieFlag<br>*Has movie flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products with movies (the link to the movies will be returned)<br>**Default Value:** <code>0</code>
pamphletFlag<br>*Pamphlet flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products with pamphlets<br>**Default Value:** <code>0</code>
appointDeliveryDateFlag<br>*Specify delivery date flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> All products<br><code>1</code> Only products for which the delivery date can be specified.<br>**Default Value:** <code>0</code>
elements<br>*Output elements* | string | Optional | Comma separated list.<br>When you specify this parameter, only those elements will be returned in the response.<br>Example: <code>elements=reviewCount,reviewAverage</code><br>**Default Value:** <code>ALL</code>
genreInformationFlag<br>*Genre information flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Do not get number of item in each genre.<br><code>1</code> Get number of item in each genre.<br>**Default Value:** <code>0</code>
tagInformationFlag<br>*Tag information flag* | integer | Optional | <br>*Valid Values:*<br><code>0</code> Do not get number of item in each tag.<br><code>1</code> Get number of item in each tag.<br>**Default Value:** <code>0</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>*Valid Values:*<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>*Valid Values:*<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/IchibaItem/Search/20140222?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=すし&hits=3
### Response

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

