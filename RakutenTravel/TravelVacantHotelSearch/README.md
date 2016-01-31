
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
infantWithMNum	<br>*Number of people (young children (meal only))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
infantWithBNum<br>*Number of people (young children (bedding only))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
infantWithoutMBNum<br>*Number of people (young children (food and bedding required))* | integer | Optional | Integer between 0 and 99.<br>{missing translation: 8～14番の各人数の合計を99人以下にする必要があります。}
roomNum<br>*Number of rooms* | integer | Optional | Integer from 1 to 10.
maxCharge	<br>*Maximum price* | long | Optional | Integer from 0 to 999999999.
minCharge<br>*Minimum price* | long | Optional | Integer from 0 to 999999999.<br>maxCharge must be greater than minCharge.
latitude<br>*Latitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example) 128,216.17<br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example) 35.6065914
longitude<br>*Longitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example) 503,259.29<br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example) 139.7513225
searchRadius<br>*Search Radius* | integer | Optional | Distance in km around latitude and longitude search.<br>Please set a value between 0.1 and 3.0.
squeezeCondition<br>*Narrowing Conditions* | string | Optional | This field allows you to specify more than one, using commas as separator.<br>Example: a non smoking room in hot spring inn: <code>squeezeCondition=kinen,onsen</code>
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.
hits<br>*How many results per page	* | integer | Optional | Parameters that determines the number of results per page.<br>Integer from 1 to 30.<br>(* 1) If the allReturnFlag was specified by the latitude and longitude search, page and the hits parameters will not be used.
page<br>*Result page	* | integer | Optional | Number of page.<br>Integer between 1 and 100.<br>* 1) If the allReturnFlag was specified by the latitude and longitude search,
searchPattern<br>*Search pattern* | integer | Optional | Parameter to specify the search pattern
hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.
responseType<br>*Response Type	* | string | Optional | Specify the amount of information returned in the response:
sort<br>*Sort* | string | Optional | 
allReturnFlag<br>*All return flag	* | integer | Optional | Flag for all cases return the information corresponding to the condition. (* 1) (* 2)<br>1: Return all results<br>(* 1) in the latitude and longitude search, responseType is small. It is only available when searchPattern is 0.<br>(* 2) If the page and hits has been specified, allReturnFlag is disabled.
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

