﻿# 1 java の基本

#### ① パッケージ宣言に関するルール
     * 1.1 必ずソースコードの先頭行に記述する
     * 1.2 前に記述できるのはコメントだけである
     * 1.3 パッケージ名.クラス名　→　完全修飾クラス名　→　名前区間を提供し、名前の衝突を避ける
     * 1.4 パッケージ単位でアクセス制御する
     * 1.5 パッケージはディレクトリ構造とマッピング
     * 1.6 クラスは必ずパッケージに所属する　ディフォルトはdefault 無名パッケージ
     * 1.7 無名パッケージに属するクラスは同じ無名パッケージに属するクラスからしかあくせすできない
#### ② インポート
     * 2.1 必ずソースコードの先頭行に記述する
     * 2.2 メソッドのstatic インポート宣言では、メソッド名にかっこ「()」や引数を付けない
     * 2.3 インポートしたクラスに、インポートされたメソッドやフィールドと同名のものがあった場合,そのインポートは無視される
     * 2.4 java コマンドでのクラス実行時に指定する起動パラメータはString配列型オブジェクトに格納されるため、1番目が配列型変数args[0]、2番目がargs[1]となる
#### ③ インポート


# 2 javaのデータ型の操作

# 3 演算子っと判定構造の使用

# 4 配列の作成と使用

# 5 ループ構造と使用

# 6 メソッドとカプセル化び操作

# 7 継承の操作

# 8 例外の処理

# 9 java APIの主要なクラス操作
#### StringBuilderクラス
#### Stringクラス
#### Predicateインタフェース
#### LocalDateクラス、LocalTimeクラス、各クラスのメソッド
#### Durationクラス、Durationクラスのメソッド
#### Periodクラス,Periodクラスのメソッド
#### DataTimeFormatterクラス、formatメソッド
#### ArrayListクラス、ArrayListクラスのメソッド	