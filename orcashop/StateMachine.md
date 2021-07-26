```uml
@startuml
 center header <size:20><b>メイン</b></size>
 [*] --> メニューバー
 state メニューバー {
   メニューバー: ID/PASS入力後「ログインボタンでログイン」,各ボタンクリックでページ間を自由に遷移
   [*] -> 商品一覧:　最初の画面
   state 商品一覧 {
    [*] --> 一覧ページ
    [*] -[dotted]-> 商品詳細ページ: 「カートの中ページ」の「詳細へ」をクリックで直接遷移
    一覧ページ -right-> 商品詳細ページ: 画像および商品名をクリック
    商品詳細ページ -left-> 一覧ページ: 「前のページに戻る」をクリック
    商品詳細ページ -right-> [*]: 「カートに入れる」をクリック
    
   }
   商品一覧 ---> カートの中:「カートに入れる」をクリック
   state カートの中 {
    [*] --> カートの中ページ
    カートの中ページ --> [*]:「詳細へ」をクリック
    カートの中ページ -> 注文確定ページ:「注文確定」をクリック 
    注文確定ページ --> [*]: 「商品一覧へ戻る」をクリック
   }
   カートの中 -up[dotted]-> 商品一覧:「詳細へ」クリック
  
   [*] -down[hidden]-> 登録情報ページ
   登録情報ページ:内容入力後「登録」をクリック
   登録情報ページ -[hidden]-> ログイン
   ログイン:「ログイン」クリック後商品一覧ページに遷移
 }
 
@enduml
```