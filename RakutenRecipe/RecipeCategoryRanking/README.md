
# Recipe/CategoryRanking

## Description

Gets the top 4 ranked recipes.
## Resource URL

https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20121121
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

categoryType<br>*Category Type* | string | Optional | Category type.<br>("all" is used when not specified)
<br>*Valid Values:*
<br><code>large</code> 
<br><code>medium</code> 
<br><code>small</code> 
<br>*Default Value:* <code>all</code>
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

https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20121121?applicationId=REPLACE_WITH_YOUR_APP_ID
### Response

```json
{
  "result": [
    {
      "recipeId": 1050000502,
      "recipeTitle": "今まで食べた大根の漬物の中で一番美味しい大根の漬物",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1050000502/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/bc0564cd6b10ee11fa5e96f5091e709b42a3aa1b.94.1.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/bc0564cd6b10ee11fa5e96f5091e709b42a3aa1b.94.1.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/bc0564cd6b10ee11fa5e96f5091e709b42a3aa1b.94.1.3.2.jpg?thum=55",
      "pickup": 0,
      "shop": 0,
      "nickname": "ｙｂｋｍｋ★",
      "recipeDescription": "簡単ですがとっても美味しいんです！！\n\n刻んでおにぎりの具材にしても◎",
      "recipeMaterial": [
        "大根",
        "★砂糖",
        "★しょうゆ",
        "★酢",
        "★昆布"
      ],
      "recipeIndication": "約30分",
      "recipeCost": "300円前後",
      "recipePublishday": "2010/12/20 23:32:19",
      "rank": "1"
    },
    {
      "recipeId": 1140021340,
      "recipeTitle": "つなぎはマヨで簡単！　蓮根はさみ照り焼き",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1140021340/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/a6a50d94d735f9dad01c9233008fb6bd587a8642.65.2.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/a6a50d94d735f9dad01c9233008fb6bd587a8642.65.2.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/a6a50d94d735f9dad01c9233008fb6bd587a8642.65.2.3.2.jpg?thum=55",
      "pickup": 1,
      "shop": 0,
      "nickname": "Slice of Coffee",
      "recipeDescription": "一人前100円以下の　胸肉、ささ身を使った蓮根はさみ照り焼きです。\nつなぎはマヨネーズなので簡単に作れます。",
      "recipeMaterial": [
        "ささ身　3本　or　胸肉(ミンチ)",
        "細ねぎ",
        "蓮根　太め",
        "塩、胡椒",
        "マヨネーズ",
        "小麦粉",
        "☆醤油",
        "☆みりん",
        "☆酒"
      ],
      "recipeIndication": "約15分",
      "recipeCost": "100円以下",
      "recipePublishday": "2014/12/22 15:21:51",
      "rank": "2"
    },
    {
      "recipeId": 1510010130,
      "recipeTitle": "HMとハチミツで簡単おいしい！炊飯器ケーキ",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1510010130/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/f8bc74536866846c7cbfae5d9a25c500a9b12cd4.43.2.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/f8bc74536866846c7cbfae5d9a25c500a9b12cd4.43.2.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/f8bc74536866846c7cbfae5d9a25c500a9b12cd4.43.2.3.2.jpg?thum=55",
      "pickup": 1,
      "shop": 0,
      "nickname": "hapihapi.jp",
      "recipeDescription": "ホットケーキミックスとハチミツでしっとりおいしいケーキか簡単に作れます。\n火加減は炊飯器にオマカセです。",
      "recipeMaterial": [
        "ホットケーキミックス",
        "ハチミツ",
        "卵",
        "塩",
        "牛乳"
      ],
      "recipeIndication": "指定なし",
      "recipeCost": "指定なし",
      "recipePublishday": "2014/05/12 17:00:45",
      "rank": "3"
    },
    {
      "recipeId": 1960000322,
      "recipeTitle": "簡単！激旨！合わせて置くだけの大根漬物",
      "recipeUrl": "http://recipe.rakuten.co.jp/recipe/1960000322/",
      "foodImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/2063225afffe7c73bb1662a0220efe1a4ddacf15.48.2.3.2.jpg",
      "mediumImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/2063225afffe7c73bb1662a0220efe1a4ddacf15.48.2.3.2.jpg?thum=54",
      "smallImageUrl": "http://image.space.rakuten.co.jp/d/strg/ctrl/3/2063225afffe7c73bb1662a0220efe1a4ddacf15.48.2.3.2.jpg?thum=55",
      "pickup": 1,
      "shop": 0,
      "nickname": "POPOTANKOBU",
      "recipeDescription": "他の料理サイトで1000件レポを頂いている自慢のお漬物です\n大根・人参‥パクパクと手が止まりません！\n食べた人が「美味しい～！」と、必ずレシピを聞いてくれます★",
      "recipeMaterial": [
        "大根",
        "◆酢",
        "◆塩",
        "◆砂糖",
        "*砂糖はお好みで調節して下さい♪",
        "◆酒",
        "お好みで（漬物昆布・ゆず皮・鷹の爪）",
        "一緒に人参・胡瓜・セロリ等漬けてもOK"
      ],
      "recipeIndication": "5分以内",
      "recipeCost": "300円前後",
      "recipePublishday": "2010/12/31 01:10:38",
      "rank": "4"
    }
  ]
}
```

