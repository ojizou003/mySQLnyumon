2023-08-13 ~ 2023-08-15
「未経験者のためのMySQL超入門」辛島信芳[著]

## SQLの基礎
- windowsのシステム環境変数でpathを登録
- cmdプロンプトで mysql -u root -pと入力して起動
- show databases;..データベース一覧の表示
- create database データベース名;..データベースの作成
- drop database データベース名;..データベースの削除
- use データベース名;..データベースの選択
- show tables;..テーブル一覧の表示
- テーブルの作成
    create table テーブル名(
      カラム名 型,
      カラム名 型,
      カラム名 型,
      ......
    );
- desc テーブル名;..カラム構成の確認(簡易版)
- show full columns from テーブル名;..カラム構成の確認
- insert into テーブル名(カラム1,カラム2,カラム3,...)values(値1,値2,値3,...);
- select*from テーブル名;..データの取得
- select カラム1,カラム2,カラム3 from テーブル名;..データの取得
- ～where 条件式;..条件指定
- update テーブル名 set カラム = 更新値,...(where 条件式);..データの更新
- delete from テーブル名(where 条件式);..データの削除
- drop table テーブル名;
- コメント文
  - #..行末までコメント
  - --..行末までコメント
  - /* コメント文 */
- order by カラム名 asc; ..昇順にソート(昇順のascは省略可)
- order by カラム名 desc ..降順にソート
- limit ..上限の指定
- limit a,b ..aからb件分
  
## 構成の追加変更
- alter table テーブル名 add カラム名;
- alter table テーブル名 change column カラム名 新カラム名 カラムの定義; ..カラムの変更
- alter table テーブル名 drop カラム名;  ..カラムの削除
- alter table 古いテーブル名 rename to 新しいテーブル名; ..テーブル名の変更

## 1歩前進
- create index インデックス名 on テーブル名 (カラム名); ..インデックスの作成
- show index from テーブル名; ..インデックスの確認
- drop index インデックス名 on テーブル名; ..インデックスの削除
- mysqldump -u ユーザー名 -p データベース名 > 出力ファイル名(バックアップファイル名) ..データのバックアップ(※mysqlを終了し、コマンドラインから入力)
- mysql -u ユーザー名 -p データベース名 < 出力ファイル名(バックアップファイル名) ..データベースの復元
- dual ..検証用ダミーテーブル
- where カラム名 like 'パターン'; ..あいまい検索
  - % ..任意の0文字以上の文字
  - _ ..任意の1文字
- null値
- 論理演算子
  - and,&&
  - or,||
  - xor ..排他的論理和、A,Bどちらかのみ条件一致
  - not
  - div ..除算(正数)
  - mod ..剰余(=%)
- 集計とグループ化
  - max()
  - min()
  - avg()
  - sum()
  - count()
  - date() ..年月日時分秒->年月日
  - group by
  - カラム名 as 別名
- テーブルの結合(join)
  - テーブル1 join テーブル2 on テーブル間の条件式

## CSV操作
- into outfile 出力ファイルパス ..ファイルへのデータ出力
  - secure-file-privの無効化
  - 区切り文字の指定
    - fields terminated by ',' ..カンマ
    - fields terminated by '\t' ..タブ
    - enclosed by '"' .."で括る
    - escaped by '"' .."をエスケープ文字に指定
- load data infile '入力ファイルパス' into table データを格納するテーブル名 ..CSVからデータを入力
- create table 作成するテーブル like 複製元のテーブル; ..テーブル構造の複製
  - insert into テーブル名 select * from コピー元のテーブル名; ..データのコピー
