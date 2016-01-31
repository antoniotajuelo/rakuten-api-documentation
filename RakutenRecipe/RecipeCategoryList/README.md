
### Recipe/CategoryList

#### Description

Gets the full recipe category list.
#### Resource URL

https://app.rakuten.co.jp/services/api/Recipe/CategoryList/20121121
#### Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

#### Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
categoryId<br>*Category ID* | string | Optional | Example:<br><code>categoryId=10</code> (large category)<br><code>categoryId=10-276</code> (medium category)<br><code>categoryId=10-276-824</code> (small category)<br>If you want to specify a medium or small category, please join the parent categories using hyphens.
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre>
#### Response Example

##### Request

https://app.rakuten.co.jp/services/api/Recipe/CategoryList/20121121?applicationId=REPLACE_WITH_YOUR_APP_ID
##### Response

```json
{
  "result": {
    "large": [
      {
        "categoryId": "30",
        "categoryName": "人気メニュー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30/"
      },
      {
        "categoryId": "31",
        "categoryName": "定番の肉料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31/"
      },
      {
        "categoryId": "32",
        "categoryName": "定番の魚料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32/"
      },
      {
        "categoryId": "33",
        "categoryName": "卵料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/33/"
      },
      {
        "categoryId": "14",
        "categoryName": "ご飯もの",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14/"
      },
      {
        "categoryId": "15",
        "categoryName": "パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15/"
      },
      {
        "categoryId": "16",
        "categoryName": "麺・粉物料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16/"
      },
      {
        "categoryId": "17",
        "categoryName": "汁物・スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17/"
      },
      {
        "categoryId": "23",
        "categoryName": "鍋料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23/"
      },
      {
        "categoryId": "18",
        "categoryName": "サラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18/"
      },
      {
        "categoryId": "22",
        "categoryName": "パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22/"
      },
      {
        "categoryId": "21",
        "categoryName": "お菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21/"
      },
      {
        "categoryId": "10",
        "categoryName": "肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10/"
      },
      {
        "categoryId": "11",
        "categoryName": "魚",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11/"
      },
      {
        "categoryId": "12",
        "categoryName": "野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12/"
      },
      {
        "categoryId": "34",
        "categoryName": "果物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/34/"
      },
      {
        "categoryId": "19",
        "categoryName": "ソース・調味料・ドレッシング",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19/"
      },
      {
        "categoryId": "27",
        "categoryName": "飲みもの",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27/"
      },
      {
        "categoryId": "35",
        "categoryName": "大豆・豆腐",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/35/"
      },
      {
        "categoryId": "13",
        "categoryName": "その他の食材",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13/"
      },
      {
        "categoryId": "20",
        "categoryName": "お弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20/"
      },
      {
        "categoryId": "36",
        "categoryName": "簡単料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/36/"
      },
      {
        "categoryId": "37",
        "categoryName": "節約料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/37/"
      },
      {
        "categoryId": "38",
        "categoryName": "今日の献立",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/38/"
      },
      {
        "categoryId": "39",
        "categoryName": "健康料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/39/"
      },
      {
        "categoryId": "40",
        "categoryName": "調理器具",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/40/"
      },
      {
        "categoryId": "26",
        "categoryName": "その他の目的・シーン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26/"
      },
      {
        "categoryId": "41",
        "categoryName": "中華料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/41/"
      },
      {
        "categoryId": "42",
        "categoryName": "韓国料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/42/"
      },
      {
        "categoryId": "43",
        "categoryName": "イタリア料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/43/"
      },
      {
        "categoryId": "44",
        "categoryName": "フランス料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/44/"
      },
      {
        "categoryId": "25",
        "categoryName": "西洋料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25/"
      },
      {
        "categoryId": "46",
        "categoryName": "エスニック料理・中南米",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/46/"
      },
      {
        "categoryId": "47",
        "categoryName": "沖縄料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/47/"
      },
      {
        "categoryId": "48",
        "categoryName": "日本各地の郷土料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/48/"
      },
      {
        "categoryId": "24",
        "categoryName": "行事・イベント",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24/"
      },
      {
        "categoryId": "49",
        "categoryName": "おせち料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/49/"
      },
      {
        "categoryId": "50",
        "categoryName": "クリスマス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/50/"
      },
      {
        "categoryId": "51",
        "categoryName": "ひな祭り",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/51/"
      },
      {
        "categoryId": "52",
        "categoryName": "春（3月～5月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/52/"
      },
      {
        "categoryId": "53",
        "categoryName": "夏（6月～8月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/53/"
      },
      {
        "categoryId": "54",
        "categoryName": "秋（9月～11月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/54/"
      },
      {
        "categoryId": "55",
        "categoryName": "冬（12月～2月）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/55/"
      }
    ],
    "medium": [
      {
        "categoryId": 275,
        "categoryName": "牛肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-275/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 276,
        "categoryName": "豚肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-276/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 277,
        "categoryName": "鶏肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-277/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 278,
        "categoryName": "ひき肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-278/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 68,
        "categoryName": "ベーコン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-68/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 66,
        "categoryName": "ソーセージ・ウインナー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-66/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 67,
        "categoryName": "ハム",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-67/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 69,
        "categoryName": "その他のお肉",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/10-69/",
        "parentCategoryId": "10"
      },
      {
        "categoryId": 70,
        "categoryName": "サーモン・鮭",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-70/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 71,
        "categoryName": "いわし",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-71/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 72,
        "categoryName": "さば",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-72/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 73,
        "categoryName": "あじ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-73/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 74,
        "categoryName": "ぶり",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-74/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 75,
        "categoryName": "さんま",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-75/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 76,
        "categoryName": "鯛",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-76/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 77,
        "categoryName": "マグロ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-77/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 443,
        "categoryName": "たら",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-443/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 78,
        "categoryName": "その他のさかな",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-78/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 80,
        "categoryName": "いか",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-80/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 81,
        "categoryName": "たこ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-81/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 79,
        "categoryName": "エビ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-79/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 83,
        "categoryName": "かに",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-83/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 444,
        "categoryName": "牡蠣",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-444/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 82,
        "categoryName": "貝類",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-82/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 445,
        "categoryName": "明太子・魚卵",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-445/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 446,
        "categoryName": "その他の魚介",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/11-446/",
        "parentCategoryId": "11"
      },
      {
        "categoryId": 447,
        "categoryName": "なす",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-447/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 448,
        "categoryName": "かぼちゃ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-448/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 449,
        "categoryName": "大根",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-449/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 450,
        "categoryName": "きゅうり",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-450/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 97,
        "categoryName": "じゃがいも",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-97/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 452,
        "categoryName": "さつまいも",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-452/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 98,
        "categoryName": "キャベツ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-98/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 453,
        "categoryName": "白菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-453/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 454,
        "categoryName": "トマト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-454/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 99,
        "categoryName": "もやし",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-99/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 456,
        "categoryName": "小松菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-456/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 457,
        "categoryName": "ほうれん草",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-457/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 455,
        "categoryName": "ごぼう",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-455/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 451,
        "categoryName": "アボカド",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-451/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 96,
        "categoryName": "玉ねぎ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-96/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 458,
        "categoryName": "ブロッコリー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-458/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 95,
        "categoryName": "にんじん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-95/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 100,
        "categoryName": "春野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-100/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 101,
        "categoryName": "夏野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-101/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 102,
        "categoryName": "秋野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-102/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 103,
        "categoryName": "冬野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-103/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 105,
        "categoryName": "きのこ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-105/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 107,
        "categoryName": "香味野菜・ハーブ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-107/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 104,
        "categoryName": "その他の野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/12-104/",
        "parentCategoryId": "12"
      },
      {
        "categoryId": 478,
        "categoryName": "もち米",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-478/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 479,
        "categoryName": "マカロニ・ペンネ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-479/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 480,
        "categoryName": "ホットケーキミックス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-480/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 481,
        "categoryName": "粉類",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-481/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 108,
        "categoryName": "練物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-108/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 109,
        "categoryName": "加工食品",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-109/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 482,
        "categoryName": "チーズ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-482/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 483,
        "categoryName": "ヨーグルト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-483/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 111,
        "categoryName": "こんにゃく",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-111/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 112,
        "categoryName": "しらたき",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-112/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 113,
        "categoryName": "海藻",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-113/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 114,
        "categoryName": "乾物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-114/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 484,
        "categoryName": "漬物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-484/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 115,
        "categoryName": "その他の食材",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/13-115/",
        "parentCategoryId": "13"
      },
      {
        "categoryId": 121,
        "categoryName": "オムライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-121/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 131,
        "categoryName": "チャーハン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-131/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 126,
        "categoryName": "パエリア",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-126/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 124,
        "categoryName": "タコライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-124/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 122,
        "categoryName": "チキンライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-122/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 123,
        "categoryName": "ハヤシライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-123/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 125,
        "categoryName": "ロコモコ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-125/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 127,
        "categoryName": "ピラフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-127/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 368,
        "categoryName": "ハッシュドビーフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-368/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 128,
        "categoryName": "その他○○ライス",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-128/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 129,
        "categoryName": "寿司",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-129/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 130,
        "categoryName": "丼物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-130/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 132,
        "categoryName": "炊き込みご飯",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-132/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 133,
        "categoryName": "おかゆ・雑炊類",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-133/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 134,
        "categoryName": "おにぎり",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-134/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 135,
        "categoryName": "アレンジごはん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-135/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 271,
        "categoryName": "その他のごはん料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/14-271/",
        "parentCategoryId": "14"
      },
      {
        "categoryId": 687,
        "categoryName": "カルボナーラ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-687/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 137,
        "categoryName": "ミートソース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-137/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 676,
        "categoryName": "ナポリタン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-676/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 681,
        "categoryName": "ペペロンチーノ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-681/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 369,
        "categoryName": "ジェノベーゼ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-369/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 677,
        "categoryName": "ペスカトーレ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-677/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 683,
        "categoryName": "たらこパスタ・明太子パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-683/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 682,
        "categoryName": "ボンゴレ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-682/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 678,
        "categoryName": "アラビアータ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-678/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 679,
        "categoryName": "トマトクリームパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-679/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 684,
        "categoryName": "納豆パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-684/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 680,
        "categoryName": "トマト系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-680/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 138,
        "categoryName": "クリーム系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-138/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 139,
        "categoryName": "オイル・塩系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-139/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 140,
        "categoryName": "チーズ系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-140/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 141,
        "categoryName": "バジルソース系パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-141/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 142,
        "categoryName": "和風パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-142/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 685,
        "categoryName": "きのこパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-685/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 686,
        "categoryName": "ツナパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-686/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 143,
        "categoryName": "冷製パスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-143/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 145,
        "categoryName": "スープスパ・スープパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-145/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 146,
        "categoryName": "その他のパスタ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-146/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 144,
        "categoryName": "パスタソース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-144/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 147,
        "categoryName": "ニョッキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-147/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 151,
        "categoryName": "ラザニア",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-151/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 382,
        "categoryName": "ラビオリ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/15-382/",
        "parentCategoryId": "15"
      },
      {
        "categoryId": 152,
        "categoryName": "うどん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-152/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 153,
        "categoryName": "蕎麦",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-153/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 154,
        "categoryName": "そうめん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-154/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 155,
        "categoryName": "焼きそば",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-155/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 156,
        "categoryName": "ラーメン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-156/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 383,
        "categoryName": "冷やし中華",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-383/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 384,
        "categoryName": "つけ麺",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-384/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 272,
        "categoryName": "その他の麺",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-272/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 385,
        "categoryName": "お好み焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-385/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 386,
        "categoryName": "たこ焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-386/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 158,
        "categoryName": "粉物料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/16-158/",
        "parentCategoryId": "16"
      },
      {
        "categoryId": 159,
        "categoryName": "味噌汁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-159/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 161,
        "categoryName": "豚汁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-161/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 387,
        "categoryName": "けんちん汁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-387/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 160,
        "categoryName": "お吸い物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-160/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 388,
        "categoryName": "かぼちゃスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-388/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 169,
        "categoryName": "野菜スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-169/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 389,
        "categoryName": "チャウダー・クラムチャウダー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-389/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 171,
        "categoryName": "コーンスープ・ポタージュ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-171/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 168,
        "categoryName": "トマトスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-168/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 167,
        "categoryName": "コンソメスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-167/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 170,
        "categoryName": "クリームスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-170/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 164,
        "categoryName": "中華スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-164/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 165,
        "categoryName": "和風スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-165/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 166,
        "categoryName": "韓国風スープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-166/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 173,
        "categoryName": "その他のスープ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-173/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 390,
        "categoryName": "ポトフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-390/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 162,
        "categoryName": "その他の汁物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/17-162/",
        "parentCategoryId": "17"
      },
      {
        "categoryId": 415,
        "categoryName": "ポテトサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-415/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 416,
        "categoryName": "春雨サラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-416/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 417,
        "categoryName": "大根サラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-417/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 418,
        "categoryName": "コールスロー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-418/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 419,
        "categoryName": "かぼちゃサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-419/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 420,
        "categoryName": "ごぼうサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-420/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 421,
        "categoryName": "マカロニサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-421/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 187,
        "categoryName": "シーザーサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-187/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 423,
        "categoryName": "コブサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-423/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 424,
        "categoryName": "タラモサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-424/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 189,
        "categoryName": "スパゲティサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-189/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 190,
        "categoryName": "ホットサラダ・温野菜",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-190/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 703,
        "categoryName": "ジャーサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-703/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 184,
        "categoryName": "素材で選ぶサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-184/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 188,
        "categoryName": "味付けで選ぶサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-188/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 185,
        "categoryName": "マヨネーズを使ったサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-185/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 186,
        "categoryName": "ナンプラーを使ったサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-186/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 191,
        "categoryName": "その他のサラダ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/18-191/",
        "parentCategoryId": "18"
      },
      {
        "categoryId": 192,
        "categoryName": "ソース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-192/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 193,
        "categoryName": "タレ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-193/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 194,
        "categoryName": "つゆ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-194/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 195,
        "categoryName": "だし",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-195/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 196,
        "categoryName": "ドレッシング",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-196/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 675,
        "categoryName": "発酵食品・発酵調味料",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-675/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 273,
        "categoryName": "その他調味料",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-273/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 274,
        "categoryName": "スパイス＆ハーブ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-274/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 463,
        "categoryName": "柚子胡椒",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-463/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 464,
        "categoryName": "オリーブオイル",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-464/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 700,
        "categoryName": "ココナッツオイル",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/19-700/",
        "parentCategoryId": "19"
      },
      {
        "categoryId": 485,
        "categoryName": "キャラ弁",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-485/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 197,
        "categoryName": "お弁当のおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-197/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 486,
        "categoryName": "運動会のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-486/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 487,
        "categoryName": "お花見のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-487/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 488,
        "categoryName": "遠足・ピクニックのお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-488/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 198,
        "categoryName": "色別おかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-198/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 199,
        "categoryName": "作り置き・冷凍できるおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-199/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 200,
        "categoryName": "すきまおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-200/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 201,
        "categoryName": "使い回しおかず",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-201/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 202,
        "categoryName": "子供のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-202/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 203,
        "categoryName": "大人のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-203/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 258,
        "categoryName": "部活のお弁当",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/20-258/",
        "parentCategoryId": "20"
      },
      {
        "categoryId": 204,
        "categoryName": "クッキー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-204/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 440,
        "categoryName": "スイートポテト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-440/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 205,
        "categoryName": "チーズケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-205/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 438,
        "categoryName": "シフォンケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-438/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 439,
        "categoryName": "パウンドケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-439/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 206,
        "categoryName": "ケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-206/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 215,
        "categoryName": "ホットケーキ・パンケーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-215/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 207,
        "categoryName": "タルト・パイ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-207/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 208,
        "categoryName": "チョコレート",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-208/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 209,
        "categoryName": "スコーン・マフィン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-209/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 210,
        "categoryName": "焼き菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-210/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 211,
        "categoryName": "プリン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-211/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 216,
        "categoryName": "ドーナツ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-216/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 212,
        "categoryName": "シュークリーム・エクレア",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-212/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 441,
        "categoryName": "ゼリー・寒天・ムース",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-441/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 442,
        "categoryName": "アイス・シャーベット",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-442/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 214,
        "categoryName": "和菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-214/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 217,
        "categoryName": "その他のお菓子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-217/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 218,
        "categoryName": "クリーム・ジャム",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/21-218/",
        "parentCategoryId": "21"
      },
      {
        "categoryId": 432,
        "categoryName": "サンドイッチ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-432/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 433,
        "categoryName": "フレンチトースト",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-433/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 434,
        "categoryName": "食パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-434/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 435,
        "categoryName": "蒸しパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-435/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 436,
        "categoryName": "ホットサンド",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-436/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 229,
        "categoryName": "惣菜パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-229/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 221,
        "categoryName": "菓子パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-221/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 220,
        "categoryName": "プレーンなパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-220/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 222,
        "categoryName": "クロワッサン・デニッシュ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-222/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 219,
        "categoryName": "ハードブレッド",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-219/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 223,
        "categoryName": "天然酵母パン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-223/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 227,
        "categoryName": "世界各国のパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-227/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 231,
        "categoryName": "ヘルシーなパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-231/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 437,
        "categoryName": "キャラパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-437/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 230,
        "categoryName": "その他のパン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/22-230/",
        "parentCategoryId": "22"
      },
      {
        "categoryId": 391,
        "categoryName": "おでん",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-391/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 392,
        "categoryName": "すき焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-392/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 393,
        "categoryName": "もつ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-393/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 394,
        "categoryName": "しゃぶしゃぶ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-394/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 395,
        "categoryName": "キムチ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-395/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 396,
        "categoryName": "湯豆腐",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-396/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 397,
        "categoryName": "豆乳鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-397/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 398,
        "categoryName": "ちゃんこ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-398/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 399,
        "categoryName": "寄せ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-399/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 400,
        "categoryName": "水炊き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-400/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 401,
        "categoryName": "トマト鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-401/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 402,
        "categoryName": "あんこう鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-402/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 403,
        "categoryName": "石狩鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-403/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 404,
        "categoryName": "カレー鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-404/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 405,
        "categoryName": "きりたんぽ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-405/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 406,
        "categoryName": "韓国鍋・チゲ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-406/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 407,
        "categoryName": "雪見鍋（みぞれ鍋）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-407/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 408,
        "categoryName": "蒸し鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-408/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 409,
        "categoryName": "ねぎま鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-409/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 410,
        "categoryName": "鴨鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-410/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 411,
        "categoryName": "カニ鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-411/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 412,
        "categoryName": "火鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-412/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 413,
        "categoryName": "牡蠣鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-413/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 698,
        "categoryName": "白味噌鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-698/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 234,
        "categoryName": "その他の鍋",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/23-234/",
        "parentCategoryId": "23"
      },
      {
        "categoryId": 631,
        "categoryName": "お食い初め料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-631/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 632,
        "categoryName": "誕生日の料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-632/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 633,
        "categoryName": "結婚記念日",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-633/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 634,
        "categoryName": "パーティー料理・ホームパーティ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-634/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 635,
        "categoryName": "子どものパーティ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-635/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 238,
        "categoryName": "バーベキュー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-238/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 244,
        "categoryName": "その他イベント",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/24-244/",
        "parentCategoryId": "24"
      },
      {
        "categoryId": 256,
        "categoryName": "スペイン料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-256/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 701,
        "categoryName": "イギリス料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-701/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 248,
        "categoryName": "ロシア料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-248/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 255,
        "categoryName": "ドイツ料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-255/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 257,
        "categoryName": "トルコ料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/25-257/",
        "parentCategoryId": "25"
      },
      {
        "categoryId": 262,
        "categoryName": "おもてなし料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-262/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 260,
        "categoryName": "おつまみ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-260/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 261,
        "categoryName": "限られた食材・調理器具で工夫",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-261/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 265,
        "categoryName": "料理のちょいテク・裏技",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/26-265/",
        "parentCategoryId": "26"
      },
      {
        "categoryId": 266,
        "categoryName": "コーヒー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-266/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 267,
        "categoryName": "お茶",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-267/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 268,
        "categoryName": "ソフトドリンク",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-268/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 465,
        "categoryName": "ジュース・スムージー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-465/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 269,
        "categoryName": "お酒",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/27-269/",
        "parentCategoryId": "27"
      },
      {
        "categoryId": 300,
        "categoryName": "ハンバーグ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-300/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 301,
        "categoryName": "餃子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-301/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 302,
        "categoryName": "肉じゃが",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-302/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 307,
        "categoryName": "カレー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-307/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 303,
        "categoryName": "牛丼",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-303/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 304,
        "categoryName": "親子丼",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-304/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 305,
        "categoryName": "豚の生姜焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-305/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 306,
        "categoryName": "グラタン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-306/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 309,
        "categoryName": "唐揚げ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-309/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 310,
        "categoryName": "コロッケ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-310/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 308,
        "categoryName": "シチュー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-308/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 311,
        "categoryName": "煮物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-311/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 312,
        "categoryName": "野菜炒め",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-312/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 313,
        "categoryName": "天ぷら",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-313/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 314,
        "categoryName": "揚げ物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-314/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 315,
        "categoryName": "豆腐料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-315/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 316,
        "categoryName": "和え物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-316/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 317,
        "categoryName": "酢の物",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/30-317/",
        "parentCategoryId": "30"
      },
      {
        "categoryId": 318,
        "categoryName": "ローストビーフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-318/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 319,
        "categoryName": "豚の角煮",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-319/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 320,
        "categoryName": "チキン南蛮",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-320/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 321,
        "categoryName": "ピーマンの肉詰め",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-321/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 323,
        "categoryName": "ロールキャベツ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-323/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 324,
        "categoryName": "スペアリブ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-324/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 325,
        "categoryName": "ローストチキン",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-325/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 326,
        "categoryName": "もつ煮込み",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-326/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 327,
        "categoryName": "ミートボール・肉団子",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-327/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 328,
        "categoryName": "ミートローフ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-328/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 329,
        "categoryName": "牛すじ煮込み",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-329/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 330,
        "categoryName": "とんかつ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-330/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 331,
        "categoryName": "ポークソテー",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-331/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 332,
        "categoryName": "つくね",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-332/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 333,
        "categoryName": "チャーシュー（焼き豚）",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-333/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 334,
        "categoryName": "煮豚",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-334/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 322,
        "categoryName": "ステーキ",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-322/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 335,
        "categoryName": "鶏肉料理",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/31-335/",
        "parentCategoryId": "31"
      },
      {
        "categoryId": 336,
        "categoryName": "ぶり大根",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-336/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 337,
        "categoryName": "ぶりの照り焼き",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-337/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 338,
        "categoryName": "さばの味噌煮",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-338/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 339,
        "categoryName": "煮魚",
        "categoryUrl": "http://recipe.rakuten.co.jp/category/32-339/",
        "parentCategoryId": "32"
      },
      {
        "categoryId": 340,
        "categoryName": "あさりの酒蒸し",
        "c
```

