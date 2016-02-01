
# AuctionGenreId/Search

## Description

Gets an auction genre's attributes, children genres and ancestor genres by auction genre id.
## Resource URL

https://app.rakuten.co.jp/services/api/AuctionGenreId/Search/20120927
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
auctionGenreId<br>*Auction Genre ID* | integer | Required | Genre ID to get information from.<br>Please use <code>0</code> for the root genre.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
genrePath<br>*Genre path* | integer | Optional | Whether or not to include genre ancestors information in the response.<br>**Valid Values:**<br><code>0</code> Do not include<br><code>1</code> Include
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/AuctionGenreId/Search/20120927?applicationId=REPLACE_WITH_YOUR_APP_ID&auctionGenreId=1150000000
### Response

```json
{
  "current": {
    "auctionGenreId": "1150000000",
    "genreName": "本・雑誌・コミック",
    "fullGenrePath": "本・雑誌・コミック",
    "genreLevel": 1,
    "hasChildFlg": 1,
    "ngRegistFlg": 1
  },
  "children": [
    {
      "child": {
        "auctionGenreId": "1150000010",
        "genreName": "漫画・コミック",
        "fullGenrePath": "本・雑誌・コミック >> 漫画・コミック",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150012740",
        "genreName": "写真集",
        "fullGenrePath": "本・雑誌・コミック >> 写真集",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150023360",
        "genreName": "詩集・句集 ",
        "fullGenrePath": "本・雑誌・コミック >> 詩集・句集 ",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150019240",
        "genreName": "ライフスタイル",
        "fullGenrePath": "本・雑誌・コミック >> ライフスタイル",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150019400",
        "genreName": "ホビー・スポーツ・美術",
        "fullGenrePath": "本・雑誌・コミック >> ホビー・スポーツ・美術",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150018590",
        "genreName": "資格・検定",
        "fullGenrePath": "本・雑誌・コミック >> 資格・検定",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150022140",
        "genreName": "エッセイ・随筆",
        "fullGenrePath": "本・雑誌・コミック >> エッセイ・随筆",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021090",
        "genreName": "科学・医学・技術",
        "fullGenrePath": "本・雑誌・コミック >> 科学・医学・技術",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021220",
        "genreName": "エンターテインメント",
        "fullGenrePath": "本・雑誌・コミック >> エンターテインメント",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021580",
        "genreName": "ライトノベル",
        "fullGenrePath": "本・雑誌・コミック >> ライトノベル",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021540",
        "genreName": "その他",
        "fullGenrePath": "本・雑誌・コミック >> その他",
        "genreLevel": 2,
        "hasChildFlg": 0,
        "ngRegistFlg": 0
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021430",
        "genreName": "洋書",
        "fullGenrePath": "本・雑誌・コミック >> 洋書",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150021420",
        "genreName": "稀覯本・絶版本・レトロ書籍",
        "fullGenrePath": "本・雑誌・コミック >> 稀覯本・絶版本・レトロ書籍",
        "genreLevel": 2,
        "hasChildFlg": 0,
        "ngRegistFlg": 0
      }
    },
    {
      "child": {
        "auctionGenreId": "1150001000",
        "genreName": "雑誌",
        "fullGenrePath": "本・雑誌・コミック >> 雑誌",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150001270",
        "genreName": "文学・小説",
        "fullGenrePath": "本・雑誌・コミック >> 文学・小説",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020070",
        "genreName": "語学・学習参考書",
        "fullGenrePath": "本・雑誌・コミック >> 語学・学習参考書",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020000",
        "genreName": "絵本・児童書・図鑑",
        "fullGenrePath": "本・雑誌・コミック >> 絵本・児童書・図鑑",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020380",
        "genreName": "旅行・留学・アウトドア",
        "fullGenrePath": "本・雑誌・コミック >> 旅行・留学・アウトドア",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020930",
        "genreName": "PC・システム開発",
        "fullGenrePath": "本・雑誌・コミック >> PC・システム開発",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020690",
        "genreName": "ビジネス・経済・就職",
        "fullGenrePath": "本・雑誌・コミック >> ビジネス・経済・就職",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    },
    {
      "child": {
        "auctionGenreId": "1150020500",
        "genreName": "人文・地歴・哲学・社会",
        "fullGenrePath": "本・雑誌・コミック >> 人文・地歴・哲学・社会",
        "genreLevel": 2,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    }
  ],
  "parents": [
    {
      "parent": {
        "auctionGenreId": "0",
        "genreName": "ルート",
        "fullGenrePath": "\\ ",
        "genreLevel": 0,
        "hasChildFlg": 1,
        "ngRegistFlg": 1
      }
    }
  ]
}
```

