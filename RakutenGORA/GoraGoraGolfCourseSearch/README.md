
# Gora/GoraGolfCourseSearch

## Description

Gets up to 30 golf courses.
## Resource URL

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseSearch/20131113
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

keyword<br>*Search keywords* | string | Optional | UTF-8 encoded string.

areaCode<br>*Area code* | integer | Optional | Code used to identify the area in Rakuten GORA.<br>If you want to examine the area code, please refer to the "Rakuten GORA Area Code List".
<br>*Default Value:* <code>0</code>
latitude<br>*Latitude* | decimal | Optional | Please enter in Japan datum

longitude<br>*Longitude* | decimal | Optional | Please enter in Japan datum

searchRadius<br>*Search Radius* | integer | Optional | Latitude and longitude radius when searching (in km)<br>It can be specified between a radius of 10 ~ 300km
<br>*Default Value:* <code>150</code>
hits<br>*How many results to display on each page* | integer | Optional | Integer of 1-30
<br>*Default Value:* <code>30</code>
page<br>*Result page* | integer | Optional | Integer of 1-100
<br>*Default Value:* <code>1</code>
sort<br>*Sort* | string | Optional | 
<br>*Valid Values:*
* <code>rating</code> Overall - Reviews of large order
* <code>50on</code> Overall - 50 alphabetical order
* <code>prefecture</code> Overall - by prefecture
* <code>highway</code> Overall - highway order
* <code>reservation</code> Overall - reservation number order
* <code>evaluation</code> Evaluation - comprehensive evaluation
* <code>staff</code> Evaluation - Staff Hospitality
* <code>facility</code> Evaluation - facilities enhancement
* <code>meal</code> Evaluation - a delicious meal
* <code>course</code> Evaluation - course / strategic
* <code>costperformance</code> Evaluation - cost performance
* <code>distance</code> Evaluation - distance is long
* <code>fairway</code> Evaluation - fairway is wide
* <code>friends</code> Recommended for - Enjoy / Casual
* <code>entertainment</code> Recommended for - entertainment / luxury
* <code>couple</code> Recommended for - couple
* <code>athlete</code> Recommended for - Athletes
* <code>beginner</code> Recommended for - novice
* <code>normal</code> Recommended for - Intermediate
* <code>senior</code> Recommended for - Advanced
* <code>woman</code> Recommended for - Women
<br>*Default Value:* <code>rating</code>
reservation<br>*Booking* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> All golf
* <code>1</code> golf course that can be reserved at Rakuten GORA only
<br>*Default Value:* <code>1</code>
carrier<br>*Platform* | integer | Optional | Whether to return information for PC or mobile phones.
<br>*Valid Values:*
* <code>0</code> PC
* <code>1</code> Mobile
<br>*Default Value:* <code>0</code>
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

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseSearch/20131113?applicationId=REPLACE_WITH_YOUR_APP_ID&hits=3
### Response

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

