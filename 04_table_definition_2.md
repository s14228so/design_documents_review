# テーブル定義書2
## 全体
- PKのカラム名はすべて「〇〇_id」ではなく「id」

## admins
- PKのINDEXに◯がない
- カラム名に接頭辞「admin_」がついているものがあるが接頭辞は必要ない

## users
- カラム名に接頭辞「user_」がついているものがあるが接頭辞は必要ない
- 「user_tel」などでカラム名に略語を使ってるが、略語は使うべきでない
- 「member_status」データ型がintegerなのにDEFAULTがfalseになっている。true or falseで管理するなら、データ型はboolean
- 「member_status」というカラム名では、会員の何のステータスを表しているか分からない
- 「user_l_kana」,「user_f_kana」では何を表しているカラム名かわかりにくいので、カラム名にnameを付け加えるべき

## ships
- PKのINDEXに◯がない
- カラム名に接頭辞「ship_」がついているものがあるが接頭辞は必要ない
- 「ship_code」とあるが,[users]と統一して「zip_code」としたほうがいい

## products
- 在庫数はカラムで管理すべきでない
- 論理削除を考慮していない

## discs
- PKのINDEXに◯がない
- FKが「products_id」となっているが、「product_id」が正しい

## songs
- 曲名をもつカラムを「song」としているが、「name」などにすべき

## labels
- レーベル名をもつカラムを「label」としているが、「name」などにすべき

## artists
- アーティスト名をもつカラムを「artist」としているが、「name」などにすべき

## genre
- ジャンル名をもつカラムを「genre」としているが、「name」などにすべき

## cart items
- テーブル名は「cart_items」が正しい
- PK「Cart item_id(正しくはid)」のINDEXに◯がない
- FKが「products_id」となっているが、「product_id」が正しい
- 「buy num」スネークケースになっていない&何を意味しているかわかりにくい

## sell_details
- テーブル名は「order_details」としたほうが、何を表しているかわかりやすい
- FKが「products_id」となっているが、「product_id」が正しい。FKに◯がない
- [sell_details]が多で[sells]が1なので、FKとして「sell_id」が必要

## sells
- テーブル名は「orders」としたほうが、何を表しているかわかりやすい
- PKのINDEXに◯がない
- [sell_details]が多で[sells]が1なのでFK「sell_details_Id」は必要ない
- 「pay」が何を意味しているかわかりにくいので、「payment_method」などにすべき
- 「total」が何を意味しているかわかりにくいので、「total_price」などにすべき