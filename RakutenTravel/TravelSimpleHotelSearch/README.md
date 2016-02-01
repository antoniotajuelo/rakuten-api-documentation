
# Travel/SimpleHotelSearch

## Description

Gets up to 30 hotels by area class code, hotel number or coordinates.
## Resource URL

https://app.rakuten.co.jp/services/api/Travel/SimpleHotelSearch/20131024
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.<br>**Valid Values:**
largeClassCode<br>*Large class code* | string | At least one is required | Code specifying the country.<br>Please get this value from the GetAreaClass API.<br>**Valid Values:**
middleClassCode<br>*Middle class code* | string | At least one is required | Code specifying the prefecture.<br>Please get this value from the GetAreaClass API.<br>**Valid Values:**
smallClassCode<br>*Small class code* | string | At least one is required | Code specifying the city.<br>Please get this value from the GetAreaClass API.<br>**Valid Values:**
detailClassCode<br>*Detail class code* | string | At least one is required | Code specifying stations or areas.<br>Please get this value from the GetAreaClass API.<br>**Valid Values:**
hotelNo<br>*Hotel Number* | integer | At least one is required | Hotel number.<br>This field allows you to specify up to 15 numbers (using commas as separator).<br>Example: <code>hotelNo=12345,54321</code><br>**Valid Values:**
latitude<br>*Latitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example: <code>128,216.17</code><br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example: <code>35.6065914</code><br>**Valid Values:**
longitude<br>*Longitude* | decimal | At least one is required | Japan datum (Tokyo Datum), in seconds, milliseconds can be specified within two decimal places.<br>Example: <code>503,259.29</code><br>However, if you specify 1 to datumType is,<br>World Geodetic System, the unit be specified in degrees.<br>Example: <code>139.7513225</code><br>**Valid Values:**
searchRadius<br>*Search Radius* | integer | Optional | Distance in km around latitude and longitude search.<br>Please set a value between 0.1 and 3.0.<br>**Valid Values:**<br>**Default Value:** <code>1</code>
squeezeCondition<br>*Narrowing Conditions* | string | Optional | This field allows you to specify more than one, using commas as separator.<br>Example: a non smoking room in hot spring inn: <code>squeezeCondition=kinen,onsen</code><br>**Valid Values:**<br><code>kinen</code> non smoking rooms<br><code>internet</code> Internet in the room<br><code>daiyoku</code> public bath<br><code>onsen</code> Onsen
carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.<br>**Valid Values:**<br><code>0</code> PC / smartphone<br><code>1</code> Mobile phones<br>**Default Value:** <code>0</code>
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.<br>**Valid Values:**<br><code>1</code> World Geodetic System.<br><code>2</code> Japan geodetic system.<br>**Default Value:** <code>2</code>
page<br>*Result page* | integer | Optional | Number of page.<br>Integer between 1 and 100.<br>* 1) If the allReturnFlag was specified by the latitude and longitude search,<br>**Valid Values:**<br>**Default Value:** <code>1</code>
hits<br>*How many results per page* | integer | Optional | Parameters that determines the number of results per page.<br>Integer from 1 to 30.<br>(* 1) If the allReturnFlag was specified by the latitude and longitude search,<br>page and the hits parameters will not be used.<br>**Valid Values:**<br>**Default Value:** <code>30</code>
hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.<br>**Valid Values:**<br><code>1</code> Small<br><code>2</code> Medium<br><code>3</code> Large<br>**Default Value:** <code>2</code>
responseType<br>*Response Type* | string | Optional | Specify the amount of information returned in the response:<br>**Valid Values:**<br><code>small</code> minimum amount of information<br><code>middle</code> standard amount of information<br><code>large</code> all the information<br>**Default Value:** <code>middle</code>
sort<br>*Sort* | string | Optional | (* 1) About "recommended order":<br>- In case of a search by facility number,<br>standard: facilities numerical order<br>- In case of search by longitude and latitude,<br>standard: order closest to farest from the specified coordinates<br>**Valid Values:**<br><code>standard</code> Recommended order (* 1)<br><code>+roomCharge</code> Best Available Rate (Low to High)<br><code>-roomCharge</code> Best Available Rate (high order)<br>**Default Value:** <code>standard</code>
allReturnFlag<br>*All return flag* | integer | Optional | Flag for returning all results. (* 1) (* 2)<br>1: return all results<br>(* 1) only valid for latitude and longitude search.<br>(* 2) If the allReturnFlag has been specified, page hits and is disabled.<br>**Valid Values:**
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.<br>**Valid Values:**
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.<br>**Valid Values:**
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code><br>**Valid Values:**
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/Travel/SimpleHotelSearch/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID&latitude=125994.28&longitude=488781.51&hits=3
### Response

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

