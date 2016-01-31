
### BooksGenre/Search

#### Description

Gets a media genre's attributes, children genres and ancestor genres by genre id.
#### Resource URL

https://app.rakuten.co.jp/services/api/BooksGenre/Search/20121128
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
booksGenreId<br>*Book genre ID* | string | Required | Genre ID to get information from.<br>Root booksGenreId is <code>000</code>.
genrePath<br>*Genre path* | integer | Optional | Whether to include ancestor genres or not in the response.<br>0: do not include ancestors<br>1: include ancestors
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/BooksGenre/Search/20121128?applicationId=REPLACE_WITH_YOUR_APP_ID&booksGenreId=001
##### Response

```json
{
  "current": {
    "booksGenreId": "001",
    "booksGenreName": "本",
    "genreLevel": 1
  },
  "children": [
    {
      "child": {
        "booksGenreId": "001001",
        "booksGenreName": "漫画（コミック）",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001002",
        "booksGenreName": "語学・学習参考書",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001003",
        "booksGenreName": "絵本・児童書・図鑑",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001004",
        "booksGenreName": "小説・エッセイ",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001005",
        "booksGenreName": "パソコン・システム開発",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001006",
        "booksGenreName": "ビジネス・経済・就職",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001007",
        "booksGenreName": "旅行・留学・アウトドア",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001008",
        "booksGenreName": "人文・思想・社会",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001009",
        "booksGenreName": "ホビー・スポーツ・美術",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001010",
        "booksGenreName": "美容・暮らし・健康・料理",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001011",
        "booksGenreName": "エンタメ・ゲーム",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001012",
        "booksGenreName": "科学・医学・技術",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001013",
        "booksGenreName": "写真集・タレント",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001016",
        "booksGenreName": "資格・検定",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001017",
        "booksGenreName": "ライトノベル",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001018",
        "booksGenreName": "楽譜",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001019",
        "booksGenreName": "文庫",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001020",
        "booksGenreName": "新書",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001021",
        "booksGenreName": "ボーイズラブ（BL）",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001022",
        "booksGenreName": "付録付き",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001023",
        "booksGenreName": "バーゲン本",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001025",
        "booksGenreName": "コミックセット",
        "genreLevel": 2
      }
    },
    {
      "child": {
        "booksGenreId": "001026",
        "booksGenreName": "カレンダー・手帳・家計簿",
        "genreLevel": 2
      }
    }
  ],
  "parents": []
}
```

