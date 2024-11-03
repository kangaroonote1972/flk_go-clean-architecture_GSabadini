# データ型
## Presenter
- input : domain model
- output : RestAPIやgRPCで定義したデータ型
  - jsonなど
- 外部に連携するためのデータ
  - メンバーの型は標準の int, string のような型
- Domainモデルを外部向けに変換する

## Domain Model
- 業務の処理で使うデータ
  - IDや重要なメンバ変数の型は独自定義したものを利用する 
- Domain Modelは直接作成せず、NewXXXというDomain modelを作成するメソッドを提供する

## Dto(Data Transfer Object)
- DBから取得した値を入れる
- Domain Modelの元ネタ。create_atのような不要な値は入れない。
- dtoをdomain modelに変換する

## リポジトリ
- input : domain model
- output : domain model
- このサンプルでは、リポジトリのインターフェースをドメインに置いている
  - ドメインが利用するものなので
- リポジトリのインターフェースをリポジトリ層に置く場合
```
repository/
  - account_repository.go (インターフェース)
infrastructure/
  - postgres/
    - account_repository.go (実装)
```


## usecase
- input : ex. json
- output : ex. json
- input, output の型はusecaseで定義


# goplaygroundによるバリデーション
https://qiita.com/RunEagler/items/ad79fc860c3689797ccc
https://tech.yappli.io/entry/go_validate

# 明示的な方アサーション : mongoHandlerはrepository.NoSQLのinterfaceを満たしている
```go
var _ repository.NoSQL = (*mongoHandler)(nil)
```
