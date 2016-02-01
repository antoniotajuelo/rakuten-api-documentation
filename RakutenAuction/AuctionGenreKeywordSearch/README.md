
# AuctionGenreKeyword/Search

## Description

Gets up to 10 auction genres by keyword.
## Resource URL

https://app.rakuten.co.jp/services/api/AuctionGenreKeyword/Search/20120927
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
keyword<br>*Genre keywords* | string | Required | Please encode the string using UTF-8.<br>Please enter between 2 and 128 characters. <br>You can use spaces for separating multiple keywords.

applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

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
## Response Example

### Request

https://app.rakuten.co.jp/services/api/AuctionGenreKeyword/Search/20120927?applicationId=REPLACE_WITH_YOUR_APP_ID&keyword=硬貨
### Response

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

