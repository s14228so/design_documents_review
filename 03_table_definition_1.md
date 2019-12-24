# テーブル定義書1
## 全体
- 指摘事項

## テーブル名
- 指摘事項

# 注意
* マークダウン形式で記入してください。
* 全体を通しての指摘事項の場合、テーブル名の部分を「全体」「共通」などとしてください。


## 全体
- idカラムが無い。
- テーブル名の最初の文字が大文字になっている。
- モデル名の記載がない。

## admins
- テーブル名はadmins
- 管理者IDのカラム名は「admin_id」ではなく「id」。

## users
- ユーザIDのカラム名は「user_id」ではなく「id」。
- 「user_f_name、user_f_kana」が空欄で登録されてしまう。
- 名前で検索できるようにするなら「user_f_name、user_l_name、user_f_kana、user_l_kana」にindexを付けるべき。
- 退会ステータスのtrueとfalseがどっちが退会を意味しているかわかりづらいので備考に書くべき。
- 配送先住所カラムと住所カラムの使い分けがわからない。配送先を複数登録したい場合もあるので配送先住所テーブルを作るべき。

## products
- 商品IDのカラム名は「product_id」ではなく「id」。
- 商品画像、refile使うのだったらカラム名は「cd_image_id」でデータ型はinteger。
- 発売日カラムが必要
- genre_id、artist_id、label_idはFK。

## discs
- ディスクナンバーを記録したいので、カラム名の「track_num」は不適切。

## songs
- disc_idのautoincrementは◯では無い。

## labels
- products_idカラムは必要ない。

## artists
- products_idカラムは必要ない。

## genres
- テーブル名はgenres
- products_idカラムは必要ない。

## cart_items
- テーブル名はcart_items
- user_idのautoincrementは◯では無い。
- products_idのデータ型が書かれていない。
- buy numではなくbuy_num
- subtotalカラムは必要ない。

## buy_details
- テーブル名はbuy_details
- buy_details_idではなくid
- buy numではなくbuy_num

## buys
- テーブル名はbuys
- buy_idではなくid
- 購入日は時間は必要ないのでデータ型はdateが適切。
