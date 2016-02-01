
# IchibaTag/Search

## Description

Gets up to 10 tags and their tag group by tag id.
## Resource URL

https://app.rakuten.co.jp/services/api/IchibaTag/Search/20140222
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
tagId<br>*Tag ID* | integer | Required | Comma-separated list of up to 10 tag IDs.

applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

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

https://app.rakuten.co.jp/services/api/IchibaTag/Search/20140222?applicationId=REPLACE_WITH_YOUR_APP_ID&tagId=1000579,1000943
### Response

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

