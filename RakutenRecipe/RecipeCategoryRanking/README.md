
# Recipe/CategoryRanking

## Description

Gets the ranking of top recipes by category.
## Resource URL

https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20170426
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
categoryId<br>*Category Id* | string | Optional | Overall ranking if omitted<br>If you specify<br>Example:<br>categoryId = 10 (major category)<br>categoryId = 10-276 (medium category)<br>categoryId = 10-276-824 (small category)<br>* Only the middle and small categories should be connected with hyphens.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>.<br>If you choose <code>json</code>, you can also set the <code>callback</code> parameter in order to use <code>jsonp</code>.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{<br>  "items": [<br>    {<br>      "item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>      }<br>    },<br>    {<br>      "item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>      }<br>    }<br>  ]<br>}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{<br>  "items": [<br>    {<br>      "itemName": "a",<br>      "itemPrice": 10<br>    },<br>    {<br>      "itemName": "b",<br>      "itemPrice": 20<br>    }<br>  ]<br>}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/Recipe/CategoryRanking/20170426?applicationId=REPLACE_WITH_YOUR_APP_ID&categoryId=10
### Response

```json
{
  "result": [
    {
      "foodImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/fbd7dd260d736654532e6c0b1ec185a0cede8675.49.2.3.2.jpg",
      "recipeDescription": "そのままでも、ご飯にのせて丼にしても♪",
      "recipePublishday": "2017/10/10 22:37:34",
      "shop": 0,
      "pickup": 0,
      "recipeId": 1760028309,
      "nickname": "はぁぽじ",
      "smallImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/fbd7dd260d736654532e6c0b1ec185a0cede8675.49.2.3.2.jpg?thum=55",
      "recipeMaterial": [
        "鶏むね肉",
        "塩",
        "酒",
        "片栗粉",
        "○水",
        "○塩",
        "○鶏がらスープの素",
        "○黒胡椒",
        "長ネギ",
        "いりごま",
        "ごま油"
      ],
      "recipeIndication": "約10分",
      "recipeCost": "300円前後",
      "rank": "1",
      "recipeUrl": "https://recipe.rakuten.co.jp/recipe/1760028309/",
      "mediumImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/fbd7dd260d736654532e6c0b1ec185a0cede8675.49.2.3.2.jpg?thum=54",
      "recipeTitle": "ご飯がすすむ！鶏むね肉のねぎ塩焼き"
    },
    {
      "foodImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/aedd5fa798b463b0371dceb8e3d0f529e4dc1b48.79.2.3.2.jpg",
      "recipeDescription": "好評の為レシピを分かりやすくしました。
分量を多少変更しました。（２０１３年３月）
以前載せていたポテサラパケットは
レシピID: 1590004701です。",
      "recipePublishday": "2012/01/27 21:13:53",
      "shop": 0,
      "pickup": 0,
      "recipeId": 1590002716,
      "nickname": "く〜-Qoo-",
      "smallImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/aedd5fa798b463b0371dceb8e3d0f529e4dc1b48.79.2.3.2.jpg?thum=55",
      "recipeMaterial": [
        "【ハンバーグ材料】",
        "牛豚合びき肉",
        "豚ひき肉",
        "玉ねぎ",
        "パン粉",
        "卵",
        "塩",
        "胡椒",
        "マヨネーズ",
        "合わせ味噌",
        "ナツメグ",
        "コーヒーフレッシュ",
        "【ハンバーグソース材料】",
        "玉ねぎ",
        "みかんやオレンジの果汁",
        "水",
        "醤油",
        "料理酒",
        "みりん",
        "【サラダ】",
        "大根",
        "人参",
        "レタスか白菜",
        "サウザンドレッシング（ダイムドレ代用）",
        "醤油マヨ",
        "炒りごま",
        "ミニトマト"
      ],
      "recipeIndication": "約1時間",
      "recipeCost": "500円前後",
      "rank": "2",
      "recipeUrl": "https://recipe.rakuten.co.jp/recipe/1590002716/",
      "mediumImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/aedd5fa798b463b0371dceb8e3d0f529e4dc1b48.79.2.3.2.jpg?thum=54",
      "recipeTitle": "元店長がこっそり教えるびっくり◯ンキーのハンバーグ"
    },
    {
      "foodImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/60a06d1b3f8929c4803550066cf33ae601f68b6c.66.2.3.2.jpg",
      "recipeDescription": "節約主婦には欠かせない
鶏のムネ肉!!
 
でもレパートリーがないし…
お腹が膨れないのは嫌だし…
時間がかかるのは面倒だし…
 
って事で簡単に美味しく!!",
      "recipePublishday": "2013/02/25 17:07:59",
      "shop": 0,
      "pickup": 1,
      "recipeId": 1100006344,
      "nickname": "かえMAMA",
      "smallImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/60a06d1b3f8929c4803550066cf33ae601f68b6c.66.2.3.2.jpg?thum=55",
      "recipeMaterial": [
        "鶏胸肉",
        "小麦粉",
        "卵",
        "▼甘酢▼",
        "砂糖",
        "酢",
        "醤油",
        "▼タルタルソース▼",
        "卵",
        "玉ねぎ",
        "マヨネーズ",
        "牛乳",
        "パセリ"
      ],
      "recipeIndication": "指定なし",
      "recipeCost": "300円前後",
      "rank": "3",
      "recipeUrl": "https://recipe.rakuten.co.jp/recipe/1100006344/",
      "mediumImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/60a06d1b3f8929c4803550066cf33ae601f68b6c.66.2.3.2.jpg?thum=54",
      "recipeTitle": "ムネ肉で‼簡単チキン南蛮♡"
    },
    {
      "foodImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/1a2766488ee9cee89e4a74365e80dc06f3581539.40.2.3.2.jpg",
      "recipeDescription": "豚バラと大根で色々とお好みの食感が楽しめます♡簡単ですがご飯のすすむ甘辛味でボリュームもありますので節約にも是非どうぞ♬",
      "recipePublishday": "2016/02/23 01:38:30",
      "shop": 0,
      "pickup": 1,
      "recipeId": 1400015997,
      "nickname": "*ももら*",
      "smallImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/1a2766488ee9cee89e4a74365e80dc06f3581539.40.2.3.2.jpg?thum=55",
      "recipeMaterial": [
        "大根",
        "豚バラ肉",
        "ゴマ油",
        "A醤油・みりん・砂糖",
        "Aみそ",
        "Aショウガ",
        "A顆粒だし"
      ],
      "recipeIndication": "約15分",
      "recipeCost": "300円前後",
      "rank": "4",
      "recipeUrl": "https://recipe.rakuten.co.jp/recipe/1400015997/",
      "mediumImageUrl": "https://image.space.rakuten.co.jp/d/strg/ctrl/3/1a2766488ee9cee89e4a74365e80dc06f3581539.40.2.3.2.jpg?thum=54",
      "recipeTitle": "簡単・節約♡テリテリ甘辛みその豚バラ大根"
    }
  ]
}
```

