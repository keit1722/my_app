# 目次

- [ER図](#ER図)
-  [テーブル設計](#テーブル設計)
- [エンドポイント & コントローラー](#エンドポイントコントローラー)


# ER図

![](https://gyazo.com/1820804839666826066a9a32d855f7b2.png)

# テーブル設計

### 登録申請

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| organization_name | string | null: false |  |
| organization_address | string | null: false | |
| organization_tel | integer | null: false | |
| user_last_name | string | null: false | |
| user_first_name | string | null: false | |
| user_email | string | null: false, index: { unique: true } | |
| slug | string | null: false, index: { unique: true } | |

### 申請アクション

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| action_type | integer | | { 承認: 1, 否認: 2 } |
| application_id | references | foreign_key: true | 外部キー |

### ユーザ招待

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| email | string | index: { unique: true } | |
| expires_at | datetime | null: false | |
| token | integer | null: false | |
| organization_id | references | foreign_key: true | 外部キー |

### 組織

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false, index: { unique: true } | |
| address | address | null: false | |
| tel | integer | null: false | |

### 組織ユーザ

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| organization_id | references | foreign_key: true | 外部キー |
| user_id | references | foreign_key: true | 外部キー |

### ユーザ

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| last_name | string | null: false | |
| first_name | string | null: false | |
| email | string | null: false, index: { unique: true } | |
| password | string | null: false | |
| crypted_password | string | null: false | |
| username | string | null: false, index: { unique: true } | |
| slug | string | null: false, index: { unique: true } | |
| role | integer | | { 一般: 1, ビジネス: 2, アドミン: 9 } |

### お気に入り

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| favoritable_id | | | ポリモーフィック |
| favoritable_type | | | ポリモーフィック |
| user_id | references | foreign_key: true | 外部キー |

### 飲食店

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |

### 宿泊施設

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |

### アクティビティ

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |

### 温泉

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |

### スキー場

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |

### フォトスポット
| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |

### ショップ

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false | |
| address | string | null: false | |
| lat | float | null: false | 緯度 |
| lng | float | null: false | 経度 |
| slug | string | null: false, index: { unique: true } | |
| detail | text | null: false | 紹介文 |
| organization_id | references | foreign_key: true | 外部キー |


### レストラン時間帯

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| restaurant_id | references | foreign_key: true | 外部キー |
| time_id | references | foreign_key: true | 外部キー |

### 時間帯

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| time_type | integer | | { breakfast: 1, lunch: 2, dinner: 9 } |

### レストランジャンルマッピング

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| restaurant_id | references | foreign_key: true | 外部キー |
| restaurant_genre_id | references | foreign_key: true | 外部キー |

### レストランジャンル

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false, index: { unique: true } | |

### 宿泊ジャンルマッピング

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| hotel_id | references | foreign_key: true | 外部キー |
| hotel_genre_id | references | foreign_key: true | 外部キー |

### 宿泊ジャンル

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false, index: { unique: true } | |

### ショップジャンルマッピング

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| shop_id | references | foreign_key: true | 外部キー |
| shop_genre_id | references | foreign_key: true | 外部キー |

### ショップジャンル

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false, index: { unique: true } | |

### リスティングエリア

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| listable_id | | | ポリモーフィック |
| listable_type | | | ポリモーフィック |
| town | integer | | { 白馬: 1, 小谷: 2 } |
| area_id | string | null: false, index: { unique: true } | |

### エリア

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| name | string | null: false, index: { unique: true } | |

### 投稿

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| postable_id | | | ポリモーフィック |
| postable_type | | | ポリモーフィック |
| title | string | null: false | |
| body | text | null: false | |

### 通知

`user_id`と`post_id`の組み合わせのユニーク制約が必要

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| user_id | string | null: false | |
| post_id | string | null: false | |
| read | boolean | null: false, default: false | |

### お気に入り

| カラム名 | データ型 | オプション | メモ |
| :--- | :--- | :--- | :--- |
| favoritable_id | | | ポリモーフィック |
| favoritable_type | | | ポリモーフィック |
| user_id | string | null: false, index: { unique: true } | |

# エンドポイント&コントローラー

| やりたいこと | HTTPメソッド | エンドポイント | コントローラ#アクション |
| :--- | :--- | :--- | :--- |
| ジャンル一覧のページを表示<br>（レストラン・宿泊施設・アクティビティなど） | GET | / | home#index |
| ログインページ表示 | GET | /login | sessions#new |
| ログインする | POST | /login | sessions#create |
| ログアウトする | DELETE | /logout | sessions#destroy |
| （本人のみ）ユーザ詳細ページ表示 | GET | /mypage/profile | mypage/users#show |
| ユーザ登録ページ表示 | GET | /signup | users#new |
| ユーザ登録処理 | POST | /mypage/profile | mypage/users#create |
| （本人のみ）ユーザ編集ページ表示 | GET | /mypage/profile/edit | mypage/users#edit |
| （本人のみ）ユーザ更新処理 | PATCH、PUT | /mypage/profile | mypage/users#update |
| 飲食店一覧ページ表示 | GET | /restaurants | restaurants#index |
| 飲食店詳細ページ表示 | GET | /restaurants/:slug | restaurants#show |
| 飲食店登録ページ表示 | GET | /business/restaurants/new | business/restaurants#new |
| 飲食店登録処理 | POST | /business/restaurants | business/restaurants#create |
| （経営者のみ）飲食店編集ページ表示 | GET | /business/restaurants/:slug/edit | business/restaurants#edit |
| （経営者のみ）飲食店更新処理 | PATCH、PUT | /business/restaurants | business/restaurants#update |
| 飲食店の投稿一覧ページ表示 | GET | /restaurants/:slug/posts | restaurants/posts#index |
| 飲食店の投稿詳細ページ表示 | GET | /restaurants/:slug/posts/:id | restaurants/posts#show |
| （経営者のみ）飲食店の投稿登録ページ表示 | GET | /business/restaurants/:slug/posts/new | business/restaurants/posts#new |
| （経営者のみ）飲食店の投稿登録処理 | POST | /business/restaurants/:slug/posts | business/restaurants/posts#create |
| （経営者のみ）飲食店の投稿編集ページ表示 | GET | /business/restaurants/:slug/posts/:id/edit | business/restaurants/posts#edit |
| （経営者のみ）飲食店の投稿更新処理 | PATCH、PUT | /business/restaurants/:slug/posts/:id | business/restaurants/posts#update |
| （経営者のみ）飲食店の投稿削除処理 | DELETE | /business/restaurants/:slug/posts/:id | business/restaurants/posts#destroy |
| お気入りに飲食店登録 | POST | /restaurants/:slug/favorite | restaurants/favorites#create |
| お気入りから飲食店削除 | DELETE | /restaurants/:slug/favorite | restaurants/favorites#destroy |
| 宿泊施設一覧ページ表示 | GET | /hotels | hotels#index |
| 宿泊施設詳細ページ表示 | GET | /hotels/:slug | hotels#show |
| 宿泊施設登録ページ表示 | GET | /business/hotels/new | business/hotels#new |
| 宿泊施設登録処理 | POST | /business/hotels | business/hotels#create |
| （経営者のみ）宿泊施設編集ページ表示 | GET | /business/hotels/:slug/edit | business/hotels#edit |
| （経営者のみ）宿泊施設更新処理 | PATCH、PUT | /business/hotels | business/hotels#update |
| 宿泊施設の投稿一覧ページ表示 | GET | /hotels/:slug/posts | hotels/posts#index |
| 宿泊施設の投稿詳細ページ表示 | GET | /hotels/:slug/posts/:id | hotels/posts#show |
| （経営者のみ）宿泊施設の投稿登録ページ表示 | GET | /business/hotels/:slug/posts/new | business/hotels/posts#new |
| （経営者のみ）宿泊施設の投稿登録処理 | POST | /business/hotels/:slug/posts | business/hotels/posts#create |
| （経営者のみ）宿泊施設の投稿編集ページ表示 | GET | /business/hotels/:slug/posts/:id/edit | business/hotels/posts#edit |
| （経営者のみ）宿泊施設の投稿更新処理 | PATCH、PUT | /business/hotels/:slug/posts/:id | business/hotels/posts#update |
| （経営者のみ）宿泊施設の投稿削除処理 | DELETE | /business/hotels/:slug/posts/:id | business/hotels/posts#destroy |
| お気入りに宿泊施設登録 | POST | /hotels/:slug/favorite | hotels/favorites#create |
| お気入りから宿泊施設削除 | DELETE | /hotels/:slug/favorite | hotels/favorites#destroy |
| アクティビティ一覧ページ表示 | GET | /activities | activities#index |
| アクティビティ詳細ページ表示 | GET | /activities/:slug | activities#show |
| アクティビティ登録ページ表示 | GET | /business/activities/new | business/activities#new |
| アクティビティ登録処理 | POST | /business/activities | business/activities#create |
| （経営者のみ）アクティビティ編集ページ表示 | GET | /business/activities/:slug/edit | business/activities#edit |
| （経営者のみ）アクティビティ更新処理 | PATCH、PUT | /business/activities | business/activities#update |
| アクティビティの投稿一覧ページ表示 | GET | /activities/:slug/posts | activities/posts#index |
| アクティビティの投稿詳細ページ表示 | GET | /activities/:slug/posts/:id | activities/posts#show |
| （経営者のみ）アクティビティの投稿登録ページ表示 | GET | /business/activities/:slug/posts/new | business/activities/posts#new |
| （経営者のみ）アクティビティの投稿登録処理 | POST | /business/activities/:slug/posts | business/activities/posts#create |
| （経営者のみ）アクティビティの投稿編集ページ表示 | GET | /business/activities/:slug/posts/:id/edit | business/activities/posts#edit |
| （経営者のみ）アクティビティの投稿更新処理 | PATCH、PUT | /business/activities/:slug/posts/:id | business/activities/posts#update |
| （経営者のみ）アクティビティの投稿削除処理 | DELETE | /business/activities/:slug/posts/:id | business/activities/posts#destroy |
| お気入りにアクティビティ登録 | POST | /activities/:slug/favorite | activities/favorites#create |
| お気入りからアクティビティ削除 | DELETE | /activities/:slug/favorite | activities/favorites#destroy |
| 温泉一覧ページ表示 | GET | /hot_springs | hot_springs#index |
| 温泉詳細ページ表示 | GET | /hot_springs/:slug | hot_springs#show |
| 温泉登録ページ表示 | GET | /business/hot_springs/new | business/hot_springs#new |
| 温泉登録処理 | POST | /business/hot_springs | business/hot_springs#create |
| （経営者のみ）温泉編集ページ表示 | GET | /business/hot_springs/:slug/edit | business/hot_springs#edit |
| （経営者のみ）温泉更新処理 | PATCH、PUT | /business/hot_springs | business/hot_springs#update |
| 温泉の投稿一覧ページ表示 | GET | /hot_springs/:slug/posts | hot_springs/posts#index |
| 温泉の投稿詳細ページ表示 | GET | /hot_springs/:slug/posts/:id | hot_springs/posts#show |
| （経営者のみ）温泉の投稿登録ページ表示 | GET | /business/hot_springs/:slug/posts/new | business/hot_springs/posts#new |
| （経営者のみ）温泉の投稿登録処理 | POST | /business/hot_springs/:slug/posts | business/hot_springs/posts#create |
| （経営者のみ）温泉の投稿編集ページ表示 | GET | /business/hot_springs/:slug/posts/:id/edit | business/hot_springs/posts#edit |
| （経営者のみ）温泉の投稿更新処理 | PATCH、PUT | /business/hot_springs/:slug/posts/:id | business/hot_springs/posts#update |
| （経営者のみ）温泉の投稿削除処理 | DELETE | /business/hot_springs/:slug/posts/:id | business/hot_springs/posts#destroy |
| お気入りに温泉登録 | POST | /hot_springs/:slug/favorite | hot_springs/favorites#create |
| お気入りから温泉削除 | DELETE | /hot_springs/:slug/favorite | hot_springs/favorites#destroy |
| フォトスポット一覧ページ表示 | GET | /photospots | photospots#index |
| フォトスポット詳細ページ表示 | GET | /photospots/:slug | photospots#show |
| フォトスポット登録ページ表示 | GET | /business/photospots/new | business/photospots#new |
| フォトスポット登録処理 | POST | /business/photospots | business/photospots#create |
| （経営者のみ）フォトスポット編集ページ表示 | GET | /business/photospots/:slug/edit | business/photospots#edit |
| （経営者のみ）フォトスポット更新処理 | PATCH、PUT | /business/photospots | business/photospots#update |
| フォトスポットの投稿一覧ページ表示 | GET | /photospots/:slug/posts | photospots/posts#index |
| フォトスポットの投稿詳細ページ表示 | GET | /photospots/:slug/posts/:id | photospots/posts#show |
| （経営者のみ）フォトスポットの投稿登録ページ表示 | GET | /business/photospots/:slug/posts/new | business/photospots/posts#new |
| （経営者のみ）フォトスポットの投稿登録処理 | POST | /business/photospots/:slug/posts | business/photospots/posts#create |
| （経営者のみ）フォトスポットの投稿編集ページ表示 | GET | /business/photospots/:slug/posts/:id/edit | business/photospots/posts#edit |
| （経営者のみ）フォトスポットの投稿更新処理 | PATCH、PUT | /business/photospots/:slug/posts/:id | business/photospots/posts#update |
| （経営者のみ）フォトスポットの投稿削除処理 | DELETE | /business/photospots/:slug/posts/:id | business/photospots/posts#destroy |
| お気入りにフォトスポット登録 | POST | /photospots/:slug/favorite | photospots/favorites#create |
| お気入りからフォトスポット削除 | DELETE | /photospots/:slug/favorite | photospots/favorites#destroy |
| スキー場一覧ページ表示 | GET | /ski_areas | ski_areas#index |
| スキー場詳細ページ表示 | GET | /ski_areas/:slug | ski_areas#show |
| スキー場登録ページ表示 | GET | /business/ski_areas/new | business/ski_areas#new |
| スキー場登録処理 | POST | /business/ski_areas | business/ski_areas#create |
| （経営者のみ）スキー場編集ページ表示 | GET | /business/ski_areas/:slug/edit | business/ski_areas#edit |
| （経営者のみ）スキー場更新処理 | PATCH、PUT | /business/ski_areas | business/ski_areas#update |
| スキー場の投稿一覧ページ表示 | GET | /ski_areas/:slug/posts | ski_areas/posts#index |
| スキー場の投稿詳細ページ表示 | GET | /ski_areas/:slug/posts/:id | ski_areas/posts#show |
| （経営者のみ）スキー場の投稿登録ページ表示 | GET | /business/ski_areas/:slug/posts/new | business/ski_areas/posts#new |
| （経営者のみ）スキー場の投稿登録処理 | POST | /business/ski_areas/:slug/posts | business/ski_areas/posts#create |
| （経営者のみ）スキー場の投稿編集ページ表示 | GET | /business/ski_areas/:slug/posts/:id/edit | business/ski_areas/posts#edit |
| （経営者のみ）スキー場の投稿更新処理 | PATCH、PUT | /business/ski_areas/:slug/posts/:id | business/ski_areas/posts#update |
| （経営者のみ）スキー場の投稿削除処理 | DELETE | /business/ski_areas/:slug/posts/:id | business/ski_areas/posts#destroy |
| お気入りにスキー場登録 | POST | /ski_areas/:slug/favorite | ski_areas/favorites#create |
| お気入りからスキー場削除 | DELETE | /ski_areas/:slug/favorite | ski_areas/favorites#destroy |
| ショップ一覧ページ表示 | GET | /shops | shops#index |
| ショップ詳細ページ表示 | GET | /shops/:slug | shops#show |
| ショップ登録ページ表示 | GET | /business/shops/new | business/shops#new |
| ショップ登録処理 | POST | /business/shops | business/shops#create |
| （経営者のみ）ショップ編集ページ表示 | GET | /business/shops/:slug/edit | business/shops#edit |
| （経営者のみ）ショップ更新処理 | PATCH、PUT | /business/shops | business/shops#update |
| ショップの投稿一覧ページ表示 | GET | /shops/:slug/posts | shops/posts#index |
| ショップの投稿詳細ページ表示 | GET | /shops/:slug/posts/:id | shops/posts#show |
| （経営者のみ）ショップの投稿登録ページ表示 | GET | /business/shops/:slug/posts/new | business/shops/posts#new |
| （経営者のみ）ショップの投稿登録処理 | POST | /business/shops/:slug/posts | business/shops/posts#create |
| （経営者のみ）ショップの投稿編集ページ表示 | GET | /business/shops/:slug/posts/:id/edit | business/shops/posts#edit |
| （経営者のみ）ショップの投稿更新処理 | PATCH、PUT | /business/shops/:slug/posts/:id | business/shops/posts#update |
| （経営者のみ）ショップの投稿削除処理 | DELETE | /business/shops/:slug/posts/:id | business/shops/posts#destroy |
| お気入りにショップ登録 | POST | /shops/:slug/favorite | shops/favorites#create |
| お気入りからショップ削除 | DELETE | /shops/:slug/favorite | shops/favorites#destroy |
| （所属ユーザのみ）組織詳細ページ表示 | GET | /mypage/organization | mypage/organizations#show |
| 組織登録ページ表示 | GET | /organizatons/new | organizations#new |
| 組織登録処理 | POST | /mypage/organization | mypage/organizations#create |
| （所属ユーザのみ）組織編集ページ表示 | GET | /mypage/organization/edit | mypage/organizations#edit |
| （所属ユーザのみ）組織更新処理 | PATCH、PUT | /mypage/organization | mypage/organizations#update |
| （ビジネスユーザのみ）ユーザ招待ページ表示 | GET | /invitations/new | invitations#new |
| （ビジネスユーザのみ）ユーザ招待録処理 | POST | /invitations | invitations#create |
| （招待されたユーザのみ）招待されたユーザの登録ページ表示 | GET | /invitations/:token/edit | invitations#edit |
| （招待されたユーザのみ）招待されたユーザの登録処理 | PATCH | /invitations/:token | invitations#update |
| 組織登録申請登録ページ表示 | GET | /registration_applications/new | registration_applications#new |
| 組織登録申請登録処理 | POST | /registration_applications | registration_applications#create |
| （管理者のみ）組織登録申請一覧ページ表示 | GET | admin/registration_applications | admin/registration_applications#index |
| （管理者のみ）組織登録申請詳細ページ表示（承認ボタンを押すページ） | GET | admin/registration_applications/:id/edit | admin/registration_applications#edit |
| （管理者のみ）組織登録申請承認処理 | PATCH、PUT | admin/registration_applications | admin/registration_applications#update |
