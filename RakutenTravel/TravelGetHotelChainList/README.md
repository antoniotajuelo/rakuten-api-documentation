
# Travel/GetHotelChainList

## Description

Gets the full hotel chain list.
## Resource URL

https://app.rakuten.co.jp/services/api/Travel/GetHotelChainList/20131024
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** No

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.
format<br>*Response format* | string | Optional | Format for the response output.<br>You can set this parameter to <code>json</code> or <code>xml</code>. JSON is usually the best option.<br>If you choose JSON, you can also set the <code>callback</code> parameter in order to use JSONP.<br>**Valid Values:**<br><code>json</code> <br><code>xml</code> <br>**Default Value:** <code>json</code>
callback<br>*Callback function name* | string | Optional | Function name to be used with the JSONP output<br>Please make sure you enter a UTF-8 URL encoded string, containing only a combination of alphanumeric characters, periods and underscores.
elements<br>*Choosing output fields* | string | Optional | By default API will return all the fields. You can specify what fields should be returned by using this parameter.<br>If you want to specify more than one parameter, please use comma (<code>,</code>) as separator.<br>For example, following request will only return <code>itemName</code>, <code>itemPrice</code> and <code>itemUrl</code>.<br><code>elements=itemName,itemPrice,itemUrl</code>
formatVersion<br>*Format version* | integer | Optional | Response format version.<br>If <code>formatVersion=2</code> is set, the response format (JSON) will be improved.<br>In case of <code>formatVersion=1</code>:<br>The API response will return an array using the following format.<br>For example, you would need to use notation <code>items[0].item.itemName</code> to access <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {"item": {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    }},<br>    {"item": {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }}<br>]}</pre><br>In case of <code>formatVersion=2</code>:<br>The API response will return an array using the following format.<br>For example, you would use the notation <code>items[0].itemName</code> to access the <code>itemName</code> parameter.<br><pre class="prettyprint">{"items": [<br>    {<br>        "itemName": "a",<br>        "itemPrice": 10<br>    },<br>    {<br>        "itemName": "b",<br>        "itemPrice": 20<br>    }<br>]}</pre><br>**Valid Values:**<br><code>1</code> <br><code>2</code> <br>**Default Value:** <code>1</code>
## Response Example

### Request

https://app.rakuten.co.jp/services/api/Travel/GetHotelChainList/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID
### Response

```json
{
  "largeClasses": [
    {
      "largeClass": [
        {
          "largeClassCode": "japan",
          "hotelChains": [
            {
              "hotelChain": {
                "hotelChainCode": "AB",
                "hotelChainName": "ABホテル",
                "hotelChainNameKana": "ABホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FUWH",
                "hotelChainName": "WHG（ワシントンホテル/ホテルグレイスリー）",
                "hotelChainNameKana": "WHG（ワシントンホテル/ホテルグレイスリー）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IHGA",
                "hotelChainName": "IHG・ANA・ホテルズグループ",
                "hotelChainNameKana": "アイエイチジーエーエヌエーホテルズグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ACH",
                "hotelChainName": "アコーホテルズ",
                "hotelChainNameKana": "アコーホテルズ",
                "hotelChainComment": "アコーホテルズは全世界で約３，８００軒のホテルを展開する世界最大級のフランスのホテルチェーンです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AS",
                "hotelChainName": "アソシアホテルズ＆リゾーツ",
                "hotelChainNameKana": "アソシアホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AP",
                "hotelChainName": "アパホテルズ＆リゾーツ",
                "hotelChainNameKana": "アパホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OR",
                "hotelChainName": "アビリタス　ホスピタリティ",
                "hotelChainNameKana": "アビリタス　ホスピタリティ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AH",
                "hotelChainName": "アベストホテルズ",
                "hotelChainNameKana": "アベストホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AMMS",
                "hotelChainName": "AMMS Hotels",
                "hotelChainNameKana": "アムスホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AMBX",
                "hotelChainName": "アンビックスグループ",
                "hotelChainNameKana": "アンビックスグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "AC",
                "hotelChainName": "アークホテルグループ(ルートインホテルズ)",
                "hotelChainNameKana": "アークホテルグループ(ルートインホテルズ)",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ART",
                "hotelChainName": "アートホテルズ",
                "hotelChainNameKana": "アートホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "UH",
                "hotelChainName": "アーバインホテルズ",
                "hotelChainNameKana": "アーバインホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RB",
                "hotelChainName": "Ｒ＆Ｂホテルチェーン（ワシントンホテル株式会社）",
                "hotelChainNameKana": "アールアンドビーホテルチェーン（ワシントンホテルカブシキガイシャ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IHG",
                "hotelChainName": "イシン・ホテルズ・グループ",
                "hotelChainNameKana": "イシン・ホテルズ・グループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ITO",
                "hotelChainName": "伊東園ホテルズ",
                "hotelChainNameKana": "イトウエンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BS",
                "hotelChainName": "インターコンチネンタルホテルズ（クラウンプラザ/ホリデイ・イン）",
                "hotelChainNameKana": "インターコンチネンタルホテルズ（クラウンプラザ/ホリデイ・イン）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IN",
                "hotelChainName": "インターコンチネンタルホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainNameKana": "インターコンチネンタルホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "EHO",
                "hotelChainName": "イーホテルチェーン",
                "hotelChainNameKana": "イーホテルチェーン",
                "hotelChainComment": "人と地球にやさしいホテル"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "WING",
                "hotelChainName": "ウィングインターナショナルホテルチェーン",
                "hotelChainNameKana": "ウィングインターナショナルホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "WTN",
                "hotelChainName": "ウェスティン ホテル＆リゾート(スターウッドホテル＆リゾート)",
                "hotelChainNameKana": "ウェスティン ホテルアンドリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PH",
                "hotelChainName": "HMIホテルグループ",
                "hotelChainNameKana": "エイチエムアイホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ANA",
                "hotelChainName": "ANAホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainNameKana": "エーエヌエーホテル（IHG・ANA・ホテルズグループ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OM",
                "hotelChainName": "大江戸温泉物語",
                "hotelChainNameKana": "オオエドオンセンモノガタリ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OD",
                "hotelChainName": "小田急グループホテル",
                "hotelChainNameKana": "オダキュウグループホテル",
                "hotelChainComment": "ホテル小田急は多彩なラインナップでビジネスやレジャーにと様々なご用途にお応えします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OK",
                "hotelChainName": "オークスグループ",
                "hotelChainNameKana": "オークスグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OHJL",
                "hotelChainName": "オークラ ニッコー ホテルズ",
                "hotelChainNameKana": "オークラ ニッコー ホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "OH",
                "hotelChainName": "オークラ ホテルズ＆リゾーツ(オークラ ニッコー ホテルズ)",
                "hotelChainNameKana": "オークラ ホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KAME",
                "hotelChainName": "ＨＯＴＥＬ　ＡＺ　グループ",
                "hotelChainNameKana": "カメノイホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KMR",
                "hotelChainName": "加森観光グループ",
                "hotelChainNameKana": "カモリカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KRKM",
                "hotelChainName": "カラカミ観光グループ",
                "hotelChainNameKana": "カラカミカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KARA",
                "hotelChainName": "唐津第一ホテルズ",
                "hotelChainNameKana": "カラツダイイチホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CA",
                "hotelChainName": "ＣＡＮＤＥＯ　ＨＯＴＥＬＳ(カンデオホテルズ)",
                "hotelChainNameKana": "カンデオホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KAMP",
                "hotelChainName": "かんぽの宿",
                "hotelChainNameKana": "カンポノヤド",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GP",
                "hotelChainName": "ガーデンパレスチェーン",
                "hotelChainNameKana": "ガーデンパレスチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "QK",
                "hotelChainName": "休暇村",
                "hotelChainNameKana": "キュウカムラ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KYGR",
                "hotelChainName": "休暇村グループの宿",
                "hotelChainNameKana": "キュウカムラグループノヤド",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KT",
                "hotelChainName": "京都タワーホテルチェーン",
                "hotelChainNameKana": "キョウトタワーホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KMHS",
                "hotelChainName": "共立メンテナンス　HOTEL＆SPA",
                "hotelChainNameKana": "キョウリツメンテナンス　ホテルアンドスパ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KRTK",
                "hotelChainName": "くれたけホテルチェーン",
                "hotelChainNameKana": "クレタケホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GI",
                "hotelChainName": "グッドイングループ",
                "hotelChainNameKana": "グッドイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GH",
                "hotelChainName": "グランパークホテルグループ",
                "hotelChainNameKana": "グランパークホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GVH",
                "hotelChainName": "グランビスタ　ホテル＆リゾート",
                "hotelChainNameKana": "グランビスタ　ホテル＆リゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GV",
                "hotelChainName": "グランヴィリオホテル(ルートインホテルズ)",
                "hotelChainNameKana": "グランヴィリオホテル(ルートインホテルズ)",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GG",
                "hotelChainName": "グリーンズホテルズ",
                "hotelChainNameKana": "グリーンズホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GHM",
                "hotelChainName": "グリーンホスピタリティーマネジメント",
                "hotelChainNameKana": "グリーンホスピタリティーマネジメント",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GHC",
                "hotelChainName": "グリーンリッチホテルズ",
                "hotelChainNameKana": "グリーンリッチホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KP",
                "hotelChainName": "京王プラザホテルチェーン",
                "hotelChainNameKana": "ケイオウプラザホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KEIO",
                "hotelChainName": "京王プレッソインチェーン",
                "hotelChainNameKana": "ケイオウプレッソインチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KKEX",
                "hotelChainName": "京急イーエックスイングループ",
                "hotelChainNameKana": "ケイキュウイーエックスイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KKR",
                "hotelChainName": "ＫＫＲホテルズ＆リゾーツ",
                "hotelChainNameKana": "ケーケーアールホテルズアンドリゾーツ",
                "hotelChainComment": "全国の観光地や主要都市に点在するKKRネットワークで観光にビジネスに皆様のお越しをお待ちしております"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KRT",
                "hotelChainName": "公立学校共済組合",
                "hotelChainNameKana": "コウリツガッコウキョウサイクミアイ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KH",
                "hotelChainName": "国際興業グループホテル",
                "hotelChainNameKana": "コクサイコウギョウグループホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KO",
                "hotelChainName": "国際ホテルグループ",
                "hotelChainNameKana": "コクサイホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CHJG",
                "hotelChainName": "コンフォートホテル",
                "hotelChainNameKana": "コンフォートホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MC",
                "hotelChainName": "コート・ホテルズ・アンド・リゾーツ",
                "hotelChainNameKana": "コート・ホテルズ・アンド・リゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SF",
                "hotelChainName": "サフィールホテルズ",
                "hotelChainNameKana": "サフィールホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SAKO",
                "hotelChainName": "三交イングループ",
                "hotelChainNameKana": "サンコウイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SH",
                "hotelChainName": "サンルートホテルチェーン",
                "hotelChainNameKana": "サンルートホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SR",
                "hotelChainName": "サンルートホテルチェーン（サンネット）",
                "hotelChainNameKana": "サンルートホテルチェーン（サンネット）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "STRW",
                "hotelChainName": "シェラトン ホテル&リゾート(スターウッドホテル＆リゾート)",
                "hotelChainNameKana": "シェラトン ホテルアンドリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SLPH",
                "hotelChainName": "シーラックパルホテルズ",
                "hotelChainNameKana": "シーラックパルホテルズ",
                "hotelChainComment": "ホテルシーラックパルは「お値段三流設備は一流」をモットーに、お客様へより快適な空間をご提供致します。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JRQ",
                "hotelChainName": "ＪＲ九州ホテルグループ",
                "hotelChainNameKana": "ジェイアールキュウシュウホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JRWN",
                "hotelChainName": "ＪＲ西日本ウェルネット（弥生会館）",
                "hotelChainNameKana": "ジェイアールニシニホンウェルネット（ヤヨイカイカン）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JW",
                "hotelChainName": "ＪＲ西日本ホテルズ",
                "hotelChainNameKana": "ジェイアールニシニホンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JRWV",
                "hotelChainName": "ジェイアール西日本ヴィアインホテルグループ",
                "hotelChainNameKana": "ジェイアールニシニホンヴィアインホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JK",
                "hotelChainName": "ＪＲ北海道グループ",
                "hotelChainNameKana": "ジェイアールホッカイドウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JASM",
                "hotelChainName": "ジャスマックグループ",
                "hotelChainNameKana": "ジャスマックグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JAL",
                "hotelChainName": "JALホテル(オークラ ニッコー ホテルズ)",
                "hotelChainNameKana": "ジャルホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JU",
                "hotelChainName": "聚楽（じゅらく）チェーン",
                "hotelChainNameKana": "ジュラク（ジュラク）チェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SKY",
                "hotelChainName": "スカイコートグループ",
                "hotelChainNameKana": "スカイコートグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SW",
                "hotelChainName": "スターウッドホテル＆リゾート",
                "hotelChainNameKana": "スターウッドホテル＆リゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "STAR",
                "hotelChainName": "スターツグループ",
                "hotelChainNameKana": "スターツグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ST",
                "hotelChainName": "スターホテルグループ",
                "hotelChainNameKana": "スターホテルグループ",
                "hotelChainComment": "旅の一等地と主要都市のベストポイント。スターホテルグループは皆さまをおもてなしいたします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SML",
                "hotelChainName": "スマイルホテル・プレミアイン",
                "hotelChainNameKana": "スマイルホテル・プレミアイン",
                "hotelChainComment": "全国に広がるスマイルホテル！ビジネスに観光に、明るい笑顔で皆様をサポートします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "VIRF",
                "hotelChainName": "住友不動産ヴィラフォンテーヌ",
                "hotelChainNameKana": "スミトモフドウサンヴィラフォンテーヌグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SPH",
                "hotelChainName": "スーパーホテル",
                "hotelChainNameKana": "スーパーホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "IZ",
                "hotelChainName": "セラヴィリゾート泉郷",
                "hotelChainNameKana": "セラヴィリゾートイズミゴウ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SI",
                "hotelChainName": "セレクト ホテルズ",
                "hotelChainNameKana": "セレクト ホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CH",
                "hotelChainName": "セントラルホテルチェーン",
                "hotelChainNameKana": "セントラルホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ZK",
                "hotelChainName": "全九州第一ホテルチェーン",
                "hotelChainNameKana": "ゼンキュウシュウダイイチホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ZN",
                "hotelChainName": "全日空ホテルズ（IHG・ANA・ホテルズグループ）",
                "hotelChainNameKana": "ゼンニックウホテルズ（アイエイチジーエーエヌエーホテルズグループ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "STF",
                "hotelChainName": "相鉄イングループ",
                "hotelChainNameKana": "ソウテツイングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CSO",
                "hotelChainName": "ソラーレコレクション（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainNameKana": "ソラーレコレクション（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DH",
                "hotelChainName": "第一寶亭留グループ",
                "hotelChainNameKana": "ダイイチホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DRNT",
                "hotelChainName": "ダイワロイネットホテルズ",
                "hotelChainNameKana": "ダイワロイネットホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DW",
                "hotelChainName": "ダイワロイヤルホテルズ",
                "hotelChainNameKana": "ダイワロイヤルホテルズ",
                "hotelChainComment": "広い客室、充実した設備・アメニティ。ワンランク上質な“やさしさ”で、お客様をお待ちしております。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "CS",
                "hotelChainName": "チサンホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainNameKana": "チサンホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TG",
                "hotelChainName": "鶴雅グループ",
                "hotelChainNameKana": "ツルガグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TE",
                "hotelChainName": "東映ホテルチェーン",
                "hotelChainNameKana": "トウエイホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TST",
                "hotelChainName": "東急ステイ",
                "hotelChainNameKana": "トウキュウステイ",
                "hotelChainComment": "広さと安心を備えた新しいスタイルの滞在空間には、充実の設備を取り揃えております。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TI",
                "hotelChainName": "東急ホテルズ",
                "hotelChainNameKana": "トウキュウホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKE",
                "hotelChainName": "東急ホテルズ（エクセルホテル東急）",
                "hotelChainNameKana": "トウキュウホテルズ（エクセルホテルトウキュウ）",
                "hotelChainComment": "洗練された現代的スタイルのスーペリアホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKI",
                "hotelChainName": "東急ホテルズ（東急REIホテル）",
                "hotelChainNameKana": "トウキュウホテルズ（トウキュウREIホテルズ）",
                "hotelChainComment": "ビジネスステイをサポートする機能的な空間のスタンダードホテル。テンピュール枕を全室に設置。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKR",
                "hotelChainName": "東急ホテルズ（パートナーズホテル）",
                "hotelChainNameKana": "トウキュウホテルズ（パートナーズホテル）",
                "hotelChainComment": "自然と調和し、日常を離れたハイグレードなくつろぎに満たされるリゾートホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKH",
                "hotelChainName": "東急ホテル（東急ホテルズ）",
                "hotelChainNameKana": "トウキュウホテル（トウキュウホテルズ）",
                "hotelChainComment": "信頼と品格のあるおもてなしのラグジュアリーホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TLND",
                "hotelChainName": "東急リゾートサービス",
                "hotelChainNameKana": "トウキュウリゾートサービス",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TB",
                "hotelChainName": "東武ホテルチェーン",
                "hotelChainNameKana": "トウブホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TY",
                "hotelChainName": "東横イン",
                "hotelChainNameKana": "トウヨコイン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "DU",
                "hotelChainName": "ドーミーイン",
                "hotelChainNameKana": "ドーミーイン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NI",
                "hotelChainName": "ナインアワーズ",
                "hotelChainNameKana": "ナインアワーズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NAQ",
                "hotelChainName": "ナクア ホテル＆リゾーツ",
                "hotelChainNameKana": "ナクア ホテル＆リゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "YM",
                "hotelChainName": "南西楽園リゾート",
                "hotelChainNameKana": "ナンセイラクエンリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NNR",
                "hotelChainName": "西鉄ホテルグループ",
                "hotelChainNameKana": "ニシテツホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NK",
                "hotelChainName": "ニッコー・ホテルズ・インターナショナル(オークラ ニッコー ホテルズ）",
                "hotelChainNameKana": "ニッコー・ホテルズ・インターナショナル",
                "hotelChainComment": "快適という名の時間。優雅なひとときをご提供するニッコー・ホテルズ・インターナショナル"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NO",
                "hotelChainName": "ニューオリエンタルホテルグループ",
                "hotelChainNameKana": "ニューオリエンタルホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NT",
                "hotelChainName": "ニューオータニホテルズ",
                "hotelChainNameKana": "ニューオータニホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NGH",
                "hotelChainName": "ニューグロリアホテルグループ",
                "hotelChainNameKana": "ニューグロリアホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NES",
                "hotelChainName": "ネストホテルグループ",
                "hotelChainNameKana": "ネストホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "NGCK",
                "hotelChainName": "野口観光グループ",
                "hotelChainNameKana": "ノグチカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HY",
                "hotelChainName": "ハイアットホテルズアンドリゾーツ",
                "hotelChainNameKana": "ハイアットホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HPR",
                "hotelChainName": "ハイパーホテルズ",
                "hotelChainNameKana": "ハイパーホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HK",
                "hotelChainName": "阪急阪神第一ホテルグループ　　",
                "hotelChainNameKana": "ハンキュウハンシンダイイチホテルグループ　　",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HTN",
                "hotelChainName": "ハートンホテルチェーン",
                "hotelChainNameKana": "ハートンホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PA",
                "hotelChainName": "パレスホテルチェーン",
                "hotelChainNameKana": "パレスホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PL",
                "hotelChainName": "パールホテルグループ",
                "hotelChainNameKana": "パールホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HI",
                "hotelChainName": "ヒルトングループ",
                "hotelChainNameKana": "ヒルトングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "VHG",
                "hotelChainName": "ビスタホテルグループ",
                "hotelChainNameKana": "ビスタホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BIG",
                "hotelChainName": "BigWeek",
                "hotelChainNameKana": "ビッグウィーク",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "VW",
                "hotelChainName": "ビューホテルズ",
                "hotelChainNameKana": "ビューホテルズ",
                "hotelChainComment": "全国に広がるビューホテルズは只今１６！真心のこもったおもてなしで快適なホテルライフをお約束致します。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MI",
                "hotelChainName": "ファミリーオ・フォルクローロ（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "ファミリーオ・フォルクローロ(ジェイアールヒガシニホンホテルズ)",
                "hotelChainComment": "ファミリーにも利用しやすい手頃な価格と親しみやすいサービスの長期滞在型ホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HATA",
                "hotelChainName": "ファミリーロッジ旅籠屋",
                "hotelChainNameKana": "ファミリーロッジハタゴヤ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FC",
                "hotelChainName": "ファーストキャビン",
                "hotelChainNameKana": "ファーストキャビン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FURI",
                "hotelChainName": "藤田観光グループ",
                "hotelChainNameKana": "フジタカンコウグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BRH",
                "hotelChainName": "ブライトンホテルズ",
                "hotelChainNameKana": "ブライトンホテルズ",
                "hotelChainComment": "総支配人の目が行き届く、パーソナルサービスの提供。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BW",
                "hotelChainName": "ブルーウェーブインホテルチェーン",
                "hotelChainNameKana": "ブルーウェーブインホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PRH",
                "hotelChainName": "プリンスホテル",
                "hotelChainNameKana": "プリンスホテル",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KEN",
                "hotelChainName": "プレミアホテルグループ",
                "hotelChainNameKana": "プレミアホテルグループ",
                "hotelChainComment": "上質かつ快適なご滞在を叶えるプレミアホテルグループ。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BWH",
                "hotelChainName": "ベストウェスタンホテルズ",
                "hotelChainNameKana": "ベストウェスタンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "SLP",
                "hotelChainName": "ベッセルホテルズ",
                "hotelChainNameKana": "ベッセルホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BHG",
                "hotelChainName": "ベネフィットホテル　グループ",
                "hotelChainNameKana": "ベネフィットホテル　グループ",
                "hotelChainComment": "お客様がどんな目的で何を求めておられるのか…その願いが叶うお手伝いをします。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HR",
                "hotelChainName": "星野リゾートグループ",
                "hotelChainNameKana": "ホシノリゾートグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "A1",
                "hotelChainName": "ホテルアルファ−ワンチェーン",
                "hotelChainNameKana": "ホテルアルファ−ワンチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GRP",
                "hotelChainName": "ホテルグリーンプラザチェーン",
                "hotelChainNameKana": "ホテルグリーンプラザチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KEI",
                "hotelChainName": "ホテル京阪チェーン",
                "hotelChainNameKana": "ホテルケイハンチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "JL",
                "hotelChainName": "ホテルＪＡＬシティ(オークラ ニッコー ホテルズ）",
                "hotelChainNameKana": "ホテルジャルシティ",
                "hotelChainComment": "明日へと繋がる空間。シティホテルの手軽さと質の高い快適なひとときをお約束するホテルJALシティ"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TKB",
                "hotelChainName": "ホテル東急ビズフォート（東急ホテルズ）",
                "hotelChainNameKana": "ホテルトウキュウビズフォート（トウキュウホテルズ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "TRST",
                "hotelChainName": "ホテルトラスティグループ",
                "hotelChainNameKana": "ホテルトラスティグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "PIN",
                "hotelChainName": "ホテルパインヒルグループ",
                "hotelChainNameKana": "ホテルパインヒルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HEJ",
                "hotelChainName": "ホテル東日本グループ",
                "hotelChainNameKana": "ホテルヒガシニホングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "HC",
                "hotelChainName": "ホテル法華クラブグループ",
                "hotelChainNameKana": "ホテルホッケクラブグループ",
                "hotelChainComment": "全国１６店舗を展開するオンリーワンなホスピタリティーホテル。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MT",
                "hotelChainName": "ホテルメッツ（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "ホテルメッツ（ジェイアールヒガシニホンホテルズ）",
                "hotelChainComment": "リーズナブルな料金、しかもシティホテル並のグレード感あふれる客室、新ビジネスクラスのホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MO",
                "hotelChainName": "ホテルモントレグループ",
                "hotelChainNameKana": "ホテルモントレグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "H3",
                "hotelChainName": "ホテルリソルチェーン",
                "hotelChainNameKana": "ホテルリソルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "H123",
                "hotelChainName": "ホテル１ー２ー３グループ",
                "hotelChainNameKana": "ホテルワンツースリーグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "WM",
                "hotelChainName": "マイステイズホテルチェーン",
                "hotelChainNameKana": "マイステイズホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MA",
                "hotelChainName": "マリオットグループ",
                "hotelChainNameKana": "マリオットグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MD",
                "hotelChainName": "マロウドチェーン",
                "hotelChainNameKana": "マロウドチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "BASE",
                "hotelChainName": "万世閣ホテルズ",
                "hotelChainNameKana": "マンセイカクホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MNTN",
                "hotelChainName": "マンテンホテルグループ",
                "hotelChainNameKana": "マンテンホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MS",
                "hotelChainName": "マークスホテルズ",
                "hotelChainNameKana": "マークスホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "GR",
                "hotelChainName": "三井ガーデンホテルズ",
                "hotelChainNameKana": "ミツイガーデンホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KI",
                "hotelChainName": "都ホテルズ＆リゾーツ",
                "hotelChainNameKana": "ミヤコホテルズアンドリゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ME",
                "hotelChainName": "名鉄ホテル旅館グループ",
                "hotelChainNameKana": "メイテツホテルリョカングループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MH",
                "hotelChainName": "メトロポリタンホテルズ（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "メトロポリタンホテルズ（ジェイアールヒガシニホンホテルズ）",
                "hotelChainComment": "駅に近く、ビジネスや観光の拠点にフットワーク抜群のシティホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MRC",
                "hotelChainName": "メルコリゾートサービス",
                "hotelChainNameKana": "メルコリゾートサービス",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MEL",
                "hotelChainName": "メルパルクチェーン",
                "hotelChainNameKana": "メルパルクチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "MB",
                "hotelChainName": "森トラスト・ホテルズ&リゾーツ",
                "hotelChainNameKana": "モリトラスト・ホテルズ&リゾーツ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "YK",
                "hotelChainName": "弥生会館（ＪＲ東日本ホテルズ）",
                "hotelChainNameKana": "ヤヨイカイカン(ジェイアールヒガシニホンホテルズ）",
                "hotelChainComment": "浜離宮の緑に囲まれ、都心にいながら自然のやすらぎに恵まれたホテルです。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "YR",
                "hotelChainName": "湯快リゾート",
                "hotelChainNameKana": "ユカイリゾート",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "UNI",
                "hotelChainName": "ユニゾホテルグループ",
                "hotelChainNameKana": "ユニゾホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "UV",
                "hotelChainName": "ユニバーサルホテルチェーン",
                "hotelChainNameKana": "ユニバーサルホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RT",
                "hotelChainName": "リステルホテルズ",
                "hotelChainNameKana": "リステルホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RI",
                "hotelChainName": "リッチホテルチェーン",
                "hotelChainNameKana": "リッチホテルチェーン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RNET",
                "hotelChainName": "リッチモンドホテルズ",
                "hotelChainNameKana": "リッチモンドホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "LM",
                "hotelChainName": "リブマックスホテルズ",
                "hotelChainNameKana": "リブマックスホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RR",
                "hotelChainName": "リーガロイヤルホテルグループ",
                "hotelChainNameKana": "リーガロイヤルホテルグループ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RE",
                "hotelChainName": "ルネッサンスホテルグループ",
                "hotelChainNameKana": "ルネッサンスホテルグループ",
                "hotelChainComment": "『駅近くリーズナブルな料金のデザイナーズホテル。広々としたバスルームが人気。』"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RU",
                "hotelChainName": "ルートイン",
                "hotelChainNameKana": "ルートイン",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RP",
                "hotelChainName": "レオパレスホテルズ",
                "hotelChainNameKana": "レオパレスホテルズ",
                "hotelChainComment": "すべてのお部屋で、オンデマンドビデオ４本・ＬＡＮ接続・ＣＳ放送が無料でご利用いただけます。"
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "ROPI",
                "hotelChainName": "ロイヤルパインズホテルズ",
                "hotelChainNameKana": "ロイヤルパインズホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "RO",
                "hotelChainName": "ロイヤルパークホテルズ",
                "hotelChainNameKana": "ロイヤルパークホテルズ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "LSH",
                "hotelChainName": "ロワジールホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainNameKana": "ロワジールホテル（ソラーレ ホテルズ アンド リゾーツ）",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "FWHP",
                "hotelChainName": "ワシントンホテルプラザ（ワシントンホテル株式会社）",
                "hotelChainNameKana": "ワシントンホテルプラザ（ワシントンホテルカブシキガイシャ",
                "hotelChainComment": ""
              }
            },
            {
              "hotelChain": {
                "hotelChainCode": "KOS",
                "hotelChainName": "ＫＯＳＣＯＩＮＮグループ",
                "hotelChainNameKana": "ＫＯＳＣＯＩＮＮグループ",
                "hotelChainComment": ""
              }
            }
          ]
        }
      ]
    }
  ]
}
```

