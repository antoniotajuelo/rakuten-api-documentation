# Rakuten Ichiba

<img alt="Rakuten Ichiba" src="./RakutenIchiba/logo.svg" width="100px">

* **Name** Rakuten Ichiba
* **URL** https://www.rakuten.co.jp/
* **Description** Rakuten's e-commerce platform.

# Endpoints

## [IchibaItem/Search](IchibaItemSearch)
Gets up to 30 items by keywords, shop, shop item code or genre.
* **Auth Type** App Key
* **Affiliation Support** Yes

## [IchibaGenre/Search](IchibaGenreSearch)
Gets a genre's attributes, tag groups, children genres, brother genres and ancestor genres by genre id.
* **Auth Type** App Key
* **Affiliation Support** No

## [IchibaTag/Search](IchibaTagSearch)
Gets up to 10 tags and their tag group by tag id.
* **Auth Type** App Key
* **Affiliation Support** No

## [IchibaItem/Ranking](IchibaItemRanking)
Gets up to 30 best seller items from all items, items from a specific genre or popular items among an age and gender demographic group.
* **Auth Type** App Key
* **Affiliation Support** Yes

## [Product/Search](ProductSearch)
Gets up to 30 products by keywords, genre or product id. Each product can be sold by one or multiple sellers and each shop can have a different price for them.
* **Auth Type** App Key
* **Affiliation Support** Yes
