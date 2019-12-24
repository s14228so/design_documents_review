# テーブル定義書1
## 全体
- PKのカラム名はすべて「〇〇_id」ではなく「id」
- テーブル名の先頭の文字が大文字になっている

## Admin
- テーブル名が単数形になっている
- 「admin_id(正しくはid)」のPK,AUTO INCREMENt,INDEXに◯が入っていない

## Users
- 「user_f_name」,「user_f_kana」の NOT NULLに◯が入っていない、意図的かもしれないが
- 「user_tel」のデータ型がstringになっているが,正しくはinteger
- 「member_status」のデータ型がstringになっているが,正しくはboolean

## Products
- 「disc_id」,「genre_id」,「label_id」,「artist_id」はFK
- 「cd_image」はrefileを使うなら「cd_image_id」とする必要がある。またデータ型はstringのほうが好ましい
- 「stock_status」のデータ型はintegerにして、enumで管理したほうがいい

## Discs
- 「disc_id(正しくはid)」のINDEXに◯がない

## Songs,Labels,Genre,Cart item
- PKである「id」が抜けている

## Songs
- 「song」のデータ型がintegerになっているが,正しくはstring

## Artists
- 「artist」のデータ型がintegerになってるが、正しくはstring
- FKはAUTO INCREMENtではない,INDEXにする必要もない

## Genre
- テーブル名が単数形になっている
- FKはAUTO INCREMENtではない,INDEXにする必要もない
- 「genre」のデータ型がintegerになってるが、正しくはstring

## Cart item
- テーブル名が単数形になっている。_で区切ってcart_itemとするのが正しい
- FKはAUTO INCREMENtではない,INDEXにする必要もない

## Buy details
- テーブル名は_で区切ってbuy_detailsとするのが正しい
- [Buy details]が多で[Buy]が1なので、FKとして「buy_id」が必要

## Buy
- テーブル名は複数形にする必要がある(buyは同士なので三単現のsをつける)
- ## Buy detailsで述べたとおり、[Buy details]が多で[Buy]が1なのでFK「buy_details_Id」は必要ない
- 「pay」のデータ型はintegerにして、enumで管理したほうがいい
- 「buy_at」はcreated_atと同じなので、必要ない
