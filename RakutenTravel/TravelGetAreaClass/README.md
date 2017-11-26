
# Travel/GetAreaClass

## Description

Gets the full area class list.
## Resource URL

https://app.rakuten.co.jp/services/api/Travel/GetAreaClass/20131024
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

https://app.rakuten.co.jp/services/api/Travel/GetAreaClass/20131024?applicationId=REPLACE_WITH_YOUR_APP_ID
### Response

```json
{
  "areaClasses": {
    "largeClasses": [
      {
        "largeClass": [
          {
            "largeClassCode": "japan",
            "largeClassName": "日本"
          },
          {
            "middleClasses": [
              {
                "middleClass": [
                  {
                    "middleClassCode": "hokkaido",
                    "middleClassName": "北海道"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sapporo",
                            "smallClassName": "札幌市内"
                          },
                          {
                            "detailClasses": [
                              {
                                "detailClass": {
                                  "detailClassCode": "A",
                                  "detailClassName": "JR札幌駅周辺・新札幌駅"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "B",
                                  "detailClassName": "大通公園周辺（テレビ塔・時計台・狸小路）"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "C",
                                  "detailClassName": "すすきの・中島公園周辺"
                                }
                              }
                            ]
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "jozankei",
                            "smallClassName": "定山渓"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "wakkanai",
                            "smallClassName": "稚内・利尻・礼文・豊富・苫前・留萌"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "abashiri",
                            "smallClassName": "網走・紋別・北見・知床"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kushiro",
                            "smallClassName": "釧路・阿寒・川湯・根室"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "obihiro",
                            "smallClassName": "帯広・十勝"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hidaka",
                            "smallClassName": "日高・えりも"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "furano",
                            "smallClassName": "富良野・美瑛・トマム"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "asahikawa",
                            "smallClassName": "旭川・層雲峡・滝川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chitose",
                            "smallClassName": "千歳・支笏・苫小牧・夕張"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "otaru",
                            "smallClassName": "小樽・余市・積丹・キロロ"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "niseko",
                            "smallClassName": "ルスツ・ニセコ・倶知安"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hakodate",
                            "smallClassName": "函館・湯の川・大沼・奥尻"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "noboribetsu",
                            "smallClassName": "登別・洞爺・室蘭"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "aomori",
                    "middleClassName": "青森県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "aomori",
                            "smallClassName": "青森市内・浅虫温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsugaru",
                            "smallClassName": "津軽半島・五所川原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ntsugaru",
                            "smallClassName": "西津軽地区"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hirosaki",
                            "smallClassName": "弘前・黒石"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "towadako",
                            "smallClassName": "八甲田・奥入瀬・十和田湖周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hachinohe",
                            "smallClassName": "八戸・三沢・古牧"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shimokita",
                            "smallClassName": "下北半島（むつ・大間）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "iwate",
                    "middleClassName": "岩手県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "morioka",
                            "smallClassName": "盛岡市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shizukuishi",
                            "smallClassName": "雫石"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "appi",
                            "smallClassName": "安比高原・八幡平・二戸"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kuji",
                            "smallClassName": "陸中海岸北部（久慈・宮古・岩泉）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ofunato",
                            "smallClassName": "陸中海岸南部（大船渡・陸前高田・釜石）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kitakami",
                            "smallClassName": "北上・花巻・遠野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ichinoseki",
                            "smallClassName": "奥州・平泉・一関"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "miyagi",
                    "middleClassName": "宮城県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sendai",
                            "smallClassName": "仙台市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "akiu",
                            "smallClassName": "秋保・作並"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "naruko",
                            "smallClassName": "鳴子・古川・くりこま高原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "matsushima",
                            "smallClassName": "松島・塩釜・石巻・南三陸・気仙沼"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shiroishi",
                            "smallClassName": "白石・宮城蔵王"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "akita",
                    "middleClassName": "秋田県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "akita",
                            "smallClassName": "秋田市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "noshiro",
                            "smallClassName": "能代・男鹿・白神"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "odate",
                            "smallClassName": "大館・鹿角・八幡平"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tazawa",
                            "smallClassName": "田沢湖・角館・大曲"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "omagari",
                            "smallClassName": "湯沢・横手"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "honjo",
                            "smallClassName": "由利本荘・鳥海山"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "yamagata",
                    "middleClassName": "山形県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yamagata",
                            "smallClassName": "山形市内・蔵王・かみのやま温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yonezawa",
                            "smallClassName": "米沢・長井・赤湯・高畠"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "murayama",
                            "smallClassName": "村山・天童"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "mogami",
                            "smallClassName": "新庄・最上・尾花沢"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shonai",
                            "smallClassName": "酒田・鶴岡・湯野浜・温海"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "hukushima",
                    "middleClassName": "福島県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fukushima",
                            "smallClassName": "福島市内・二本松"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "aizu",
                            "smallClassName": "会津若松・喜多方"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "bandai",
                            "smallClassName": "猪苗代・表磐梯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "urabandai",
                            "smallClassName": "磐梯高原・裏磐梯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "koriyama",
                            "smallClassName": "郡山・磐梯熱海"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "minami",
                            "smallClassName": "南会津（下郷・只見・檜枝岐村）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nakadori",
                            "smallClassName": "須賀川・白河"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hamadori",
                            "smallClassName": "浜通り（いわき・南相馬・相馬）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "ibaragi",
                    "middleClassName": "茨城県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "mito",
                            "smallClassName": "水戸・笠間"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "oarai",
                            "smallClassName": "大洗・ひたちなか"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hitachi",
                            "smallClassName": "日立・北茨城・奥久慈"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsukuba",
                            "smallClassName": "つくば・土浦・取手"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yuki",
                            "smallClassName": "結城・筑西・古河"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsuchiura",
                            "smallClassName": "鹿嶋・潮来・北浦"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "tochigi",
                    "middleClassName": "栃木県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "utsunomiya",
                            "smallClassName": "宇都宮・さくら"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nikko",
                            "smallClassName": "日光・中禅寺湖・今市"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kinugawa",
                            "smallClassName": "鬼怒川・川治・湯西川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nasu",
                            "smallClassName": "那須・板室・黒磯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shiobara",
                            "smallClassName": "塩原・矢板・大田原・西那須野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "mashiko",
                            "smallClassName": "益子･真岡・茂木"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "koyama",
                            "smallClassName": "小山・足利・栃木・佐野"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "gunma",
                    "middleClassName": "群馬県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "maebashi",
                            "smallClassName": "前橋市内（赤城高原含む）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ikaho",
                            "smallClassName": "伊香保温泉・渋川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "manza",
                            "smallClassName": "万座･嬬恋･北軽井沢"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kusatsu",
                            "smallClassName": "草津・白根"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shimaonsen",
                            "smallClassName": "四万温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "numata",
                            "smallClassName": "水上・猿ヶ京・沼田"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "oze",
                            "smallClassName": "尾瀬・丸沼"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kiryu",
                            "smallClassName": "桐生・伊勢崎・太田・館林"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "takasaki",
                            "smallClassName": "高崎市街"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fujioka",
                            "smallClassName": "藤岡・妙義・安中・磯部温泉"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "saitama",
                    "middleClassName": "埼玉県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "saitama",
                            "smallClassName": "さいたま（大宮・浦和）・川口・上尾"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kasukabe",
                            "smallClassName": "草加・春日部・羽生"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kumagaya",
                            "smallClassName": "熊谷・深谷・本庄"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kawagoe",
                            "smallClassName": "川越・和光・東松山・志木"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tokorozawa",
                            "smallClassName": "所沢・狭山・飯能"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chichibu",
                            "smallClassName": "秩父・長瀞"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "tiba",
                    "middleClassName": "千葉県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chiba",
                            "smallClassName": "千葉市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "keiyo",
                            "smallClassName": "舞浜・船橋・幕張"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kashiwa",
                            "smallClassName": "松戸・柏・佐倉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "narita",
                            "smallClassName": "成田空港周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "choshi",
                            "smallClassName": "銚子・佐原・東金・九十九里"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sotobo",
                            "smallClassName": "外房（鴨川・勝浦・御宿・茂原・養老渓谷）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tateyama",
                            "smallClassName": "南房総（館山・白浜･千倉）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "uchibo",
                            "smallClassName": "内房（市原・木更津・君津・富津）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "tokyo",
                    "middleClassName": "東京都"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tokyo",
                            "smallClassName": "東京２３区内"
                          },
                          {
                            "detailClasses": [
                              {
                                "detailClass": {
                                  "detailClassCode": "A",
                                  "detailClassName": "東京駅・銀座・日本橋・秋葉原"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "B",
                                  "detailClassName": "新橋・汐留・お台場"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "C",
                                  "detailClassName": "赤坂・六本木・麻布・永田町"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "D",
                                  "detailClassName": "渋谷・青山・恵比寿・目黒"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "E",
                                  "detailClassName": "品川・蒲田・羽田空港"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "F",
                                  "detailClassName": "新宿・中野・杉並"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "G",
                                  "detailClassName": "池袋・赤羽・板橋・練馬"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "H",
                                  "detailClassName": "御茶ノ水・水道橋・飯田橋"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "I",
                                  "detailClassName": "上野・浅草・両国・足立"
                                }
                              },
                              {
                                "detailClass": {
                                  "detailClassCode": "J",
                                  "detailClassName": "江東・江戸川・新小岩"
                                }
                              }
                            ]
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nishi",
                            "smallClassName": "東京西部（立川・八王子・町田・府中・吉祥寺）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "okutama",
                            "smallClassName": "奥多摩・青梅・羽村"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ritou",
                            "smallClassName": "八丈島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "oshima",
                            "smallClassName": "大島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kouzu",
                            "smallClassName": "神津島・新島・式根島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "miyake",
                            "smallClassName": "三宅島"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "Ogasawara",
                            "smallClassName": "小笠原諸島"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "kanagawa",
                    "middleClassName": "神奈川県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yokohama",
                            "smallClassName": "横浜市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kawasaki",
                            "smallClassName": "川崎市内"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hakone",
                            "smallClassName": "箱根"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "odawara",
                            "smallClassName": "小田原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yugawara",
                            "smallClassName": "湯河原・真鶴"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sagamiko",
                            "smallClassName": "相模湖・丹沢"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sagamihara",
                            "smallClassName": "相模原･大和"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ebina",
                            "smallClassName": "海老名・厚木・伊勢原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shonan",
                            "smallClassName": "湘南（鎌倉・藤沢・茅ヶ崎・平塚・江ノ島・大磯）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "miura",
                            "smallClassName": "三浦半島（横須賀・三浦）"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "niigata",
                    "middleClassName": "新潟県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "niigata",
                            "smallClassName": "新潟市"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kaetsu",
                            "smallClassName": "新発田（月岡）・村上（瀬波）・咲花"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kita",
                            "smallClassName": "長岡・燕・三条・寺泊"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "minami",
                            "smallClassName": "魚沼・十日町・津南・六日町・大湯温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yuzawa",
                            "smallClassName": "湯沢･苗場"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "joetsu",
                            "smallClassName": "柏崎・上越・妙高・糸魚川"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sado",
                            "smallClassName": "佐渡"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "toyama",
                    "middleClassName": "富山県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "toyama",
                            "smallClassName": "富山市･八尾･立山山麓"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "goto",
                            "smallClassName": "滑川・魚津・黒部・宇奈月"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gosei",
                            "smallClassName": "高岡・砺波・新湊・氷見・小矢部・射水"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "ishikawa",
                    "middleClassName": "石川県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kanazawa",
                            "smallClassName": "金沢市内・周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kaga",
                            "smallClassName": "加賀（山代・山中・片山津）・小松（粟津）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "noto",
                            "smallClassName": "能登・輪島・珠洲"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nanao",
                            "smallClassName": "七尾・和倉・羽咋"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "hukui",
                    "middleClassName": "福井県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hukui",
                            "smallClassName": "福井市"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "awara",
                            "smallClassName": "あわら・三国"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "katsuyama",
                            "smallClassName": "永平寺・勝山・大野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "echizen",
                            "smallClassName": "越前・鯖江・武生"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tsuruga",
                            "smallClassName": "敦賀・美浜"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "obama",
                            "smallClassName": "若狭・小浜・高浜"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "yamanasi",
                    "middleClassName": "山梨県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kofu",
                            "smallClassName": "甲府市内・昇仙峡・甲斐"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yamanashi",
                            "smallClassName": "山梨・石和・勝沼・塩山"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "otsuki",
                            "smallClassName": "大月・都留"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fujisan",
                            "smallClassName": "富士吉田・忍野・山中湖・富士山"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kawaguchiko",
                            "smallClassName": "河口湖・西湖・精進湖・本栖湖"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "minobu",
                            "smallClassName": "身延・下部温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nirasaki",
                            "smallClassName": "韮崎・南アルプス"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kiyosato",
                            "smallClassName": "八ヶ岳・小淵沢・清里・大泉"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "nagano",
                    "middleClassName": "長野県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nagano",
                            "smallClassName": "長野"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "madara",
                            "smallClassName": "斑尾・黒姫・飯綱･戸隠"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nozawa",
                            "smallClassName": "野沢温泉・木島平・戸狩"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shiga",
                            "smallClassName": "志賀高原･湯田中･渋"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ueda",
                            "smallClassName": "上田・別所・鹿教湯"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "chikuma",
                            "smallClassName": "戸倉上山田・千曲"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "sugadaira",
                            "smallClassName": "菅平・峰の原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "karui",
                            "smallClassName": "軽井沢・佐久･小諸"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yatsu",
                            "smallClassName": "八ヶ岳（野辺山･富士見高原･原村）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kirigamine",
                            "smallClassName": "白樺湖・車山・蓼科・霧ヶ峰"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "suwa",
                            "smallClassName": "諏訪湖周辺"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ina",
                            "smallClassName": "伊那・飯田・駒ヶ根・昼神"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kiso",
                            "smallClassName": "木曽"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "matsumo",
                            "smallClassName": "松本・浅間温泉・塩尻"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kamiko",
                            "smallClassName": "上高地・白骨・乗鞍"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hotaka",
                            "smallClassName": "豊科・穂高・安曇野・大町"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hakuba",
                            "smallClassName": "白馬・小谷"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "gihu",
                    "middleClassName": "岐阜県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gifu",
                            "smallClassName": "岐阜・各務原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kamitakara",
                            "smallClassName": "奥飛騨・新穂高"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "takayama",
                            "smallClassName": "高山・飛騨"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gero",
                            "smallClassName": "下呂温泉・濁河温泉"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "tajimi",
                            "smallClassName": "多治見・恵那・中津川・美濃加茂・可児"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "gujo",
                            "smallClassName": "郡上八幡・関・美濃"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shirakawago",
                            "smallClassName": "白川郷"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ogaki",
                            "smallClassName": "大垣・岐阜羽島"
                          }
                        ]
                      }
                    ]
                  }
                ]
              },
              {
                "middleClass": [
                  {
                    "middleClassCode": "shizuoka",
                    "middleClassName": "静岡県"
                  },
                  {
                    "smallClasses": [
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shizuoka",
                            "smallClassName": "静岡市（静岡・清水）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "atami",
                            "smallClassName": "熱海"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "ito",
                            "smallClassName": "伊東"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "izukogen",
                            "smallClassName": "伊豆高原"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "higashi",
                            "smallClassName": "東伊豆・河津"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "shimoda",
                            "smallClassName": "下田・南伊豆"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "nishi",
                            "smallClassName": "西伊豆（戸田・土肥･堂ヶ島・松崎）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "naka",
                            "smallClassName": "中伊豆（伊豆長岡・修善寺・天城湯ヶ島）"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "fuji",
                            "smallClassName": "富士・富士宮"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "numazu",
                            "smallClassName": "三島・沼津・御殿場"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "yaizu",
                            "smallClassName": "焼津・藤枝・御前崎・寸又峡"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "hamamatsu",
                            "smallClassName": "浜松・浜名湖・天竜"
                          }
                        ]
                      },
                      {
                        "smallClass": [
                          {
                            "smallClassCode": "kikugawa",
                            "
```

