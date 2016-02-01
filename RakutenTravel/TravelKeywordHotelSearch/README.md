
# Travel/KeywordHotelSearch

## Description

Gets up to 30 hotels by keyword.
## Resource URL

https://app.rakuten.co.jp/services/api/Travel/KeywordHotelSearch/20131024
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
keyword<br>*Search Keyword* | string | Required | When you specify more than one keyword separated by an space character it is considered an AND search.<br>Your search must contain at least 2 characters.

applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

carrier<br>*Platform* | integer | Optional | Whether to return information for PC/smartphone or mobile phone.
<br>*Valid Values:*
<br><code>0</code> PC / smartphone
<br><code>1</code> Mobile phones
<br>*Default Value:* <code>0</code>
page<br>*Result page* | integer | Optional | Number of page.<br>Integer between 1 and 100.
<br>*Default Value:* <code>1</code>
hits<br>*How many results per page* | integer | Optional | Parameters that determines the number of results per page.<br>Integer from 1 to 30.
<br>*Default Value:* <code>30</code>
datumType<br>*Latitude and longitude type* | integer | Optional | It specifies the latitude and longitude type of input and output parameters.
<br>*Valid Values:*
<br><code>1</code> World Geodetic System.
<br><code>2</code> Japan geodetic system.
<br>*Default Value:* <code>2</code>
middleClassCode<br>*Middle class code* | string | Optional | Code specifying the prefecture.<br>Please get this value from the GetAreaClass API.

searchField<br>*Search scope* | integer | Optional | Specify the target scope of the keyword search.
<br>*Valid Values:*
<br><code>0</code> hotel name, the plan name or the room names
<br><code>1</code> Hotel Name Only
<br>*Default Value:* <code>0</code>
hotelChainCode<br>*Hotel chain code* | string | Optional | Code for specifying the hotel chain.<br>If this field is specified, only hotels belonging to the specified hotel chain will be searched.<br>Please get the hotel chain list from the GetHotelChainList API.<br>This field allows you to specify up to 5 hotel chains separated by commas.<br>Example: <code>hotelChainCode=JL,NK</code>

hotelThumbnailSize<br>*Hotel Thumbnail Size* | integer | Optional | Specify the image size of the hotel image thumbnail URL of the output parameters.
<br>*Valid Values:*
<br><code>1</code> Small
<br><code>2</code> Medium
<br><code>3</code> Large
<br>*Default Value:* <code>2</code>
responseType<br>*Response Type* | string | Optional | Specify the amount of information returned in the response:
<br>*Valid Values:*
<br><code>small</code> minimum amount of information
<br><code>middle</code> standard amount of information
<br><code>large</code> all the information
<br>*Default Value:* <code>middle</code>
sort<br>*Sort* | string | Optional | 
<br>*Valid Values:*
<br><code>standard</code> keyword predictive value in descending order
<br><code>+roomCharge</code> Best Available Rate (Low to High)
<br><code>-roomCharge</code> Best Available Rate (high order)
<br>*Default Value:* <code>standard</code>
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

