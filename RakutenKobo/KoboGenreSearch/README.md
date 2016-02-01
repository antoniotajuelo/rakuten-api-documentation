
# Kobo/GenreSearch

## Description

Gets a Kobo genre's attributes, children genres and ancestor genres by Kobo genre id.
## Resource URL

https://app.rakuten.co.jp/services/api/Kobo/GenreSearch/20131010
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.<br>**Valid Values:**
koboGenreId<br>*Kobo Genre ID* | string | Optional | Kobo genre ID.<br>koboGenreId = 101 is the parent genre.<br>**Valid Values:**<br>**Default Value:** <code>101</code>
genrePath<br>*Genre path* | integer | Optional | Whether or not to include a the ancestor genres in the result set:<br>**Valid Values:**<br><code>0</code> do not include ancestors<br><code>1</code> include ancestors<br>**Default Value:** <code>0</code>
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.<br>**Valid Values:**
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code><br>**Valid Values:**
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/Kobo/GenreSearch/20131010?applicationId=REPLACE_WITH_YOUR_APP_ID&koboGenreId=101901
### Response

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

