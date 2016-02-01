
# Gora/GoraGolfCourseDetail

## Description

Gets a golf course details by a golf course id.
## Resource URL

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseDetail/20140410
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
golfCourseId<br>*Golf course ID* | long | Required | You can get this value from the output of Rakuten GORA golf Search API (GoraGolfCourceSearch)

applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

carrier<br>*Platform* | integer | Optional | Whether to request information for PC or mobile phone usage:
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

https://app.rakuten.co.jp/services/api/Gora/GoraGolfCourseDetail/20140410?applicationId=REPLACE_WITH_YOUR_APP_ID&golfCourseId=80004
### Response

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

