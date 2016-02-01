
# Travel/HotelDetailSeach

## Description

Gets a hotel details by hotel number.
## Resource URL

https://app.rakuten.co.jp/services/api/Travel/HotelDetailSearch/20131024
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

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
## Response Example

### Request

https://app.rakuten.co.jp/services/api/Travel/HotelDetailSearch/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID&hotelNo=136197
### Response

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

