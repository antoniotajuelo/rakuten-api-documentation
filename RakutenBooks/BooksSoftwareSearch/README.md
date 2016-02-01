
# BooksSoftware/Search

## Description

Gets up to 30 software items by title, OS, maker, label, JAN or genre.
## Resource URL

https://app.rakuten.co.jp/services/api/BooksSoftware/Search/20130522
## Resource Information

* **Auth Type** App Key
* **Affiliation Support** Yes

## Parameters

Name | Type | Required | Description
 --- | --- | --- | --- 
applicationId<br>*App ID* | string | Required | The Application ID that identifies your application. You can get it from <a href="https://webservice.rakuten.co.jp/" target="_blank">https://webservice.rakuten.co.jp/</a>.

title<br>*Software Title* | string | At least one is required | Keywords to search from the software title.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.

os<br>*Supported OS* | string | At least one is required | Search for supported OS (operating system).<br>This string needs to be UTF-8 encoded.

makerCode<br>*MPN (Manufacturer Part Number)* | string | At least one is required | Search for MPN (Manufacturer Part Number).<br>This string needs to be UTF-8 encoded.

label<br>*Publisher name* | string | At least one is required | Keywords to search from publisher releasing the items.<br>This string needs to be UTF-8 encoded.<br>If you want to use multiple keywords in your search, please separate them using spaces.

jan<br>*Software JAN code* | long | At least one is required | Search for a software JAN code.

booksGenreId<br>*Book genre ID* | string | At least one is required | Use it for narrow results to a specific book genre ID.<br>Only genres under bookGenreId = 004 (software) are valid.<br>Please use the Book Genre Search API to look up book genre names and genre relations.<br>Please note that this genre is different from the Rakuten Ichiba genre.
<br>*Default Value:* <code>004</code>
hits<br>*How many results to display on each page* | integer | Optional | An integer between 1 and 30.
<br>*Default Value:* <code>30</code>
page<br>*Result page* | integer | Optional | An integer between 1 and 100.
<br>*Default Value:* <code>1</code>
availability<br>*Availability* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> all items
* <code>1</code> In Stock
* <code>2</code> Usually ships in about 3 to 7 days
* <code>3</code> Usually ships in about 3 to 9 days
* <code>4</code> Manufacturer stock
* <code>5</code> Preorder
* <code>6</code> Check stock with manufacturer
<br>*Default Value:* <code>0</code>
outOfStockFlag<br>*Out of Stock Flag* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> Do not include out of stock items.
* <code>1</code> Include out of stock items.
<br>*Default Value:* <code>0</code>
sort<br>*Sort* | string | Optional | *UTF-8 URL encoding is required.
<br>*Valid Values:*
* <code>standard</code> 
* <code>sales</code> 
* <code>+releaseDate</code> Release date (Ascending order)
* <code>-releaseDate</code> Release date (Descending order)
* <code>+itemPrice</code> Item price (Ascending order)
* <code>-itemPrice</code> Item price (Descending order)
* <code>reviewCount</code> 
* <code>reviewAverage</code> 
<br>*Default Value:* <code>standard</code>
limitedFlag<br>*Limited Flag* | integer | Optional | ※ Limited Edition include products such as limited time, limited quantity or reservation limited.
<br>*Valid Values:*
* <code>0</code> All items
* <code>1</code> Limited Edition only
<br>*Default Value:* <code>0</code>
carrier<br>*Platform* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> PC
* <code>1</code> Mobile
<br>*Default Value:* <code>0</code>
genreInformationFlag<br>*Genre information flag	* | integer | Optional | 
<br>*Valid Values:*
* <code>0</code> Do not get number of item in each genre.
* <code>1</code> Get number of item in each genre.
<br>*Default Value:* <code>0</code>
affiliateId<br>*Affiliate ID* | string | Optional | If this endpoint supports affiliation, here you can enter your affiliate ID. If you do, the links in the API response will include your affiliate ID.

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

https://app.rakuten.co.jp/services/api/BooksSoftware/Search/20130522?applicationId=REPLACE_WITH_YOUR_APP_ID&os=mac&hits=3
### Response

```json
{
  "count": 468,
  "page": 1,
  "first": 1,
  "last": 3,
  "hits": 3,
  "carrier": 0,
  "pageCount": 100,
  "Items": [
    {
      "Item": {
        "title": "BiND for WebLiFE 8 プロフェッショナル Macintosh 解説本付き",
        "titleKana": "バインド フォー ウェブライフ 8 プロフェッショナル マッキントッシュ カイセツボンツキ",
        "os": "Mac",
        "label": "",
        "jan": "4527956025056",
        "makerCode": "DSP-02505",
        "itemCaption": "PCもスマホもすぐさま、思いのままに。\n初めてでも自在にアレンジ。PCサイトを自動でスマホに最適化\n\nBiND は、HTMLやCSSなどの専門知識がなくてもデザイン性の高いウェブサイトが構築可能。\n高品質かつ豊富なテンプレートと特許取得の独自のブロック編集によって自在なカスタマイズ性が実現し、\nウェブ制作の初心者から作業効率を重視するプロのデザイナーに至るまで広く活用されています。\n多くのお客様からのご要望にお応えして「BiND8 解説本バンドル版」発売！\n\n※収録テンプレート数219サイト（WordPress、Facebookページ含む）\n※WebLiFE*サーバー ベーシックコース24ヶ月+プレミアムコース3ヶ月 無料\n※Smooth Contact プロコース（980円／月）1年間利用権付\n※BiND8ガイドブック 「BiND8の教科書」\n\n【レスポンシブWebへ対応】\nPCサイトをスマホサイトに自動で最適化。\n閲覧するデバイスのサイズに合わせて自動でレイアウトを最適表示する、レスポンシブ対応のWebサイトが作れるようになりました。\nレスポンシブ対応のテンプレート（全20種62カラーバリエ）を使って作る手軽さに加え、\nページの編集エリアを指す「ブロック」単位で表示の有無を設定できるため、PCとスマホとで情報量のコントロールも可能です。\n両サイトをプレビューしながら作れるため調整もしやすく便利です。\n\n【統制されたデザインで見やすさ倍増】\nCSS設定を一括で行える新機能「Dress」を搭載。Webデザインを制御するCSSを一括して設定可能。\n「Dress」機能では、カラー、フォント、余白などサイト全体に掛るCSS設定の入った20種のDressテンプレートから選べるほか、\nユーザーが任意に設定し保存することもできます。\nデザインカスタマイズする際にも、統制感をキープしながらアレンジしていくことができ、\nWebデザインに不慣れな方でもデザインが崩れにくく、情報の見やすいWebサイトが作れます。\n\n【高性能フォームを美しいデザインで】\nセキュリティ万全なフォーム「Smooth Contact」が始動。\nSSLに対応した、機能もデザインも高性能なフォームサービスが始まります。\n問い合わせ状況は専用の管理画面で確認でき、メール転送も可能な高性能なフォームサービスが、\n公開サーバーに関係なく、かつ無料で利用できる環境を用意しました。\nサイトデザインに合わせたオリジナルのフォームが実装可能となります。\n\n【BiNDの構造を抜本的に見直し、飛躍的に進化】\n操作UIを刷新！ユーザビリティを大きく向上\nこれまでのリッチインターフェースから、シンプルな見た目に一新し、あらゆる基本編集機能を改善。\nよく使う機能をより使いやすく、作業パフォーマンスが向上します。\nBiNDのサイト制作で要となるブロック編集の最小単位「ブロック」のコピー機能や、\n作成したページを別サイトにも移行できる機能のほか、検索機能が充実しました。",
        "salesDate": "2015年12月18日",
        "itemPrice": 33264,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13517578/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "004319007007"
      }
    },
    {
      "Item": {
        "title": "Tri-folding Bluetooth Keyboard シャンパンゴールド GK930-CG",
        "titleKana": "トリホールディング ブルートゥース キーボード シャンパンゴールド",
        "os": "Mac",
        "label": "",
        "jan": "4582159571342",
        "makerCode": "GK930-CG",
        "itemCaption": "●スマホやタブレットに最適！折り畳み式Bluetoothキーボード\n・三つ折りタイプだから実現できた、コンパクトながらもワイドで使いやすい設計\n・場所を問わずいつでもどこでもスマホやタブレットでのタイピングが快適に\n・Bluetoothは端末と一度ペアリングしておけば次回以降、電源ONで自動的に接続\n\n●抜群の打ちやすさで快適なタイピングを実現\n・17.5mmのワイドなキーピッチ、1.8mmのキーストロークで快適にタイピング可能\n・シームレス構造により、折り畳み部分のつなぎ目を気にせずタイピング可能\n\n●使いやすさにこだわった設計\n・本体背面のアルミ素材により、デザイン性だけでなく軽量化も実現\n・キーボードの開閉で電源が自動でON／OFFになるオートウェイク機能搭載\n\n●マルチOS対応！タブレットもスマホもOSを問わずこれ1台でOK\n・各OSに対応したファンクションキーを搭載、ボタン一つでOSモードの切換が可能\n・日本語配列に対応する記号キーを別色で印字！iOSは勿論、AndroidやWindowsでもOSによる配列認識を気にせずタイピング可能\n\n●軽量コンパクト設計で持ち運びに最適\n・重量は310g、収納時のサイズは149mm×100mmと持ち運びに便利な軽量コンパクト設計\n・乾電池ではなくリチウムイオンバッテリー内蔵のため薄型設計を実現\n・2時間の充電で約60時間の連続使用が可能、一度の充電だけで長期間使用もOK\n\n●対応OS：Windows 8〜8.1／Android OS4.1以降／iOS6以降　\n●キータイプ：パンタグラフ　\n●キー配列：64キー（英語配列）　\n●キーピッチ： 17.5mm ／ キーストローク：1.8mm　\n●サイズ（使用時）：252×92×10mm ／ サイズ（収納時）：145×92×18mm \n●本体重量：184g　\n●USBインターフェース：Micro USB　\n●電源：リチウムイオン電池（内臓）　\n●充電時間：約2時間 ／ 連続使用時間：約65時間 ／ 待受時間：約100日間\n●接続方式： Bluetooth Ver. 3.0　\n●接続距離：10m　\n●製品内容：Bluetoothワイヤレスキーボード、USBケーブル（キーボード充電用）、ユーザーガイド、製品保証書（保証期間：1年）\n※本製品は技適（TELEC）認証を取得しています",
        "salesDate": "2015年12月25日",
        "itemPrice": 10778,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13517547/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "004322002"
      }
    },
    {
      "Item": {
        "title": "BiND for WebLiFE 8 スタンダード Macintosh 解説本付き",
        "titleKana": "バインド フォー ウェブライフ 8 スタンダード マッキントッシュ カイセツボンツキ",
        "os": "Mac",
        "label": "",
        "jan": "4527956024059",
        "makerCode": "DSP-02405",
        "itemCaption": "初めてでも自在にアレンジ。PCサイトを自動でスマホに最適化\n\nBiND は、HTMLやCSSなどの専門知識がなくてもデザイン性の高いウェブサイトが構築可能。\n高品質かつ豊富なテンプレートと特許取得の独自のブロック編集によって自在なカスタマイズ性が実現し、\nウェブ制作の初心者から作業効率を重視するプロのデザイナーに至るまで広く活用されています。\n多くのお客様からのご要望にお応えして「BiND8 解説本バンドル版」発売！\n\n※収録テンプレート数180サイト\n※WebLiFE*サーバー ベーシックコース6ヶ月 無料\n※Smooth Contact フリーコースが利用可能\n※BiND8ガイドブック 「BiND8の教科書」\n\n【レスポンシブWebへ対応。伝わりやすいWebへ】\nPCサイトをスマホサイトに自動で最適化。\n閲覧するデバイスのサイズに合わせて自動でレイアウトを最適表示する、レスポンシブ対応のWebサイトが作成できる！\nレスポンシブ対応のテンプレート（全20種62カラーバリエ）を使って作る手軽さに加え、\nページの編集エリアを指す「ブロック」単位で表示の有無を設定できるため、PCとスマホとで情報量のコントロールも可能。\n両サイトをプレビューしながら作れるため調整もしやすく便利です。\n\n【統制されたデザインで見やすさ倍増】\nCSS設定を一括で行える新機能「Dress」を搭載。Webデザインを制御するCSSを一括して設定可能。\n「Dress」機能では、カラー、フォント、余白などサイト全体に掛るCSS設定の入った20種のDressテンプレートから選べるほか、\nユーザーが任意に設定し保存することもできます。\nデザインカスタマイズする際にも、統制感をキープしながらアレンジしていくことができ、\nWebデザインに不慣れな方でもデザインが崩れにくく、情報の見やすいWebサイトが作れます。\n\n【高性能フォームを美しいデザインで】\nセキュリティ万全なフォーム「Smooth Contact」が始動。\nSSLに対応した、機能もデザインも高性能なフォームサービスが始まります。\n問い合わせ状況は専用の管理画面で確認でき、メール転送も可能な高性能なフォームサービスが、\n公開サーバーに関係なく、かつ無料で利用できる環境を用意。\nサイトデザインに合わせたオリジナルのフォームが実装可能。\n\n【BiNDの構造を抜本的に見直し、飛躍的に進化】\n操作UIを刷新！ユーザビリティを大きく向上\nBiNDが登場して以来初となる、ユーザーインターフェースを刷新。\nこれまでのリッチインターフェースから、シンプルな見た目に一新し、あらゆる基本編集機能の改善を図りました。\nよく使う機能をより使いやすく、作業パフォーマンスが向上します。\nBiNDのサイト制作で要となるブロック編集の最小単位「ブロック」のコピー機能や、\n作成したページを別サイトにも移行できる機能のほか、検索機能が充実。",
        "salesDate": "2015年12月18日",
        "itemPrice": 22464,
        "listPrice": 0,
        "discountRate": 0,
        "discountPrice": 0,
        "itemUrl": "http://books.rakuten.co.jp/rb/13517577/",
        "affiliateUrl": "",
        "smallImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=64x64",
        "mediumImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=120x120",
        "largeImageUrl": "http://thumbnail.image.rakuten.co.jp/@0_mall/book/cabinet/noimage_01.gif?_ex=200x200",
        "availability": "5",
        "postageFlag": 2,
        "limitedFlag": 0,
        "reviewCount": 0,
        "reviewAverage": "0.0",
        "booksGenreId": "004319007007"
      }
    }
  ],
  "GenreInformation": []
}
```

