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
- テーブル名と同じワードを含むカラム名は改名する必要がある。

## admins
- テーブル名はadmins
- 管理者IDのカラム名は「admin_id」ではなく「id」。
- 管理者idカラムのPKに○が必要。

## users
- ユーザIDのカラム名は「user_id」ではなく「id」。
- 「user_f_name、user_f_kana」が空欄で登録されてしまう。
- 名前で検索できるようにするなら「user_f_name、user_l_name、user_f_kana、user_l_kana」にindexを付けるべき。
- 「user_f_name、user_l_name、user_f_kana、user_l_kana」に関して、lやfのように略さず、last、firstと記述するべき。
- 退会ステータスのtrueとfalseがどっちが退会を意味しているかわかりづらいので備考に書くべき。さらにデータ型はBooleanが適切。
- 配送先住所カラムと住所カラムの使い分けがわからない。配送先を複数登録したい場合もあるので配送先住所テーブルを作るべき。
- 電話番号や郵便番号のデータ型はstringが適切。integerだと0から始まる数列を正しく認識できない。

## products
- 商品IDのカラム名は「product_id」ではなく「id」。
- 商品画像、refile使うのだったらカラム名は「cd_image_id」でデータ型はinteger。
- 発売日カラムが必要
- genre_id、artist_id、label_idはFK。
- stock_statusは在庫数がわかればわかるので不要。
- stockは（入荷数 - 購買数）で計算できるので不要。

## discs
- ディスクの順番を記録したいので、カラム名の「track_num」は不適切。orderやdisc_numberなどが適切。
- 複数枚組を考慮してない。

## songs
- disc_idのautoincrementは◯では無い。
- songカラムが曲名をもたせるのに、integerとなってる。
- songカラムが曲名を持つなら、カラム名はnameが適切。

## labels
- products_idカラムは必要ない。
- labelカラムがレーベル名を持つなら、カラム名はnameが適切。

## artists
- products_idカラムは必要ない。
- artistsカラムがアーティスト名を持つなら、カラム名はnameが適切。
- artistsカラムがアーティスト名を持たせるのに、integerとなっている。

## genres
- テーブル名はgenres
- products_idカラムは必要ない。
- genreカラムがジャンル名を持つなら、カラム名はnameが適切。
- genreカラムがジャンル名を持たせるのに、integerとなっている。

## cart_items
- テーブル名はcart_items
- user_idのautoincrementは◯では無い。
- products_idのデータ型が書かれていない。
- buy numではなくbuy_num
- subtotalカラムは必要ない。

## buy_details
- テーブル名の単語と単語の間にアンダーバーがない。
- テーブル名はoreder_detailsが適切。それに伴い、カラム名もbuy_numからorder_num、order_amount、amountなどに変更。
- buy_details_idではなくid

## buys
- テーブル名は複数形。
- テーブル名はorderが適切。
- buy_idではなくid
- 購入日は時間は必要ないのでデータ型はdateが適切。
- 郵便番号と住所のカラムが必要。
- 支払い方法カラムはpaymentが適切。また、enumを使用するためデータ型はintegerが適切。
- 支払い合計カラムのカラム名が不適切。priceなどが適切。




# フィードバック1回目
[add]→付け加えなければいけないところ
[fix]→修正が必要なところ
[comment]→その他コメント（修正ではないけど、確認して欲しいポイントです）

## 全体
- モデル名の記載がない。
[fix]→テーブル名のみを書き出せばいいので、モデル名は必要のないように思われ。
[add]→テーブル名と同じワードを含む、カラムは改名する必要がある。
[add]→user_l_nameのlのような略語は使わない。この場合、きちんとlastと書くことを指摘。


## admins
[add]→PKにまるがついてないことも指摘。

## users
- 退会ステータスのtrueとfalseがどっちが退会を意味しているかわかりづらいので備考に書くべき。
[fix]→かつ、データ型がstringになってしまっている。
[add]→電話番号や郵便番号がintegerになっている。0始まりの数列が正しく認識されなくなる


## products
[add]→在庫数が分かれば、在庫状況はわかる為、不要。
[add]→在庫数は計算された値なので、廃止。（入荷数）ー（購買数）で計算できるため。

## discs
[add]→ディスクの順番はどのように管理するか
[add]→複数枚組を考慮してない。

## songs
[add]→songカラムが曲名をもつならば命名はnameなどとするべき。
[add]→songカラムが曲名をもたせるのに、integerとなってる。

## labels
[add]→labelカラムがレーベル名をもつならばnameなどとするべき

## artists
[add]→artistカラムがアーティスト名をもつならばnameなどとするべき
[add]→artistカラムが曲名をもたせるのに、integerとなってる。


## genres
[add]→genreカラムがジャンル名をもつならばnameなどとするべき
[add]→genreカラムが曲名をもたせるのに、integerとなってる。

## buy_details
- buy numではなくbuy_num
[fix]→そもそもbuy_numだと、意味が通らず、命名に問題あり。
[add]→buy_detailsだと受注詳細の意味じゃない。命名は「管理者の立場で行う」「動詞は不適。名詞にする。」そもそも「買う」では意味が通らない。「受注」「注文」と言った言葉に変更。

## buys
[add]→buyだと受注の意味じゃない。命名は「管理者の立場で行う」「動詞は不適。名詞にする。」そもそも「買う」では意味が通らない。「受注」「注文」と言った言葉に変更。
[add]→送付先住所はあるが、郵便番号と住所がない
[add]→支払い方法がstringになっており、enumを考慮してない。また、カラム名の命名も不適。
[add]→stock =　「支払い合計」？命名がおかしい。

# フィードバック2回目
[add]→付け加えなければいけないところ
[fix]→修正が必要なところ
[comment]→その他コメント（修正ではないけど、確認して欲しいポイントです）

## discs
[add]→複数枚組を考慮してない。

# フィードバック3回目
[add]→付け加えなければいけないところ
[fix]→修正が必要なところ
[comment]→その他コメント（修正ではないけど、確認して欲しいポイントです）

- 合格です！！
