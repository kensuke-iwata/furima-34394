# テーブル設計

## users テーブル

| Column               | Type    | Options                   |
| -------------------- | ------- | --------------------------|
| nickname             | string  | null: false               |
| email                | string  | null: false, unique :true |
| encrypted_password   | string  | null: false               |
| family_name          | string  | null: false               |
| first_name           | string  | null: false               |
| family_name_kana     | string  | null: false               |
| first_name_kana      | string  | null: false               |
| birth_day            | date    | null: false               |

### Association 

- has_many :items
- has_many :buys

## items テーブル

| Column      | Type        | Options                        |
| ----------- | ----------- | ------------------------------ |
| name        | string      | null: false                    |
| description | string      | null: false                    |
| category_id | integer     | null: false                    |
| status_id   | integer     | null: false                    |
| cost_id     | integer     | null: false                    |
| area_id     | integer     | null: false                    |
| day_id      | integer     | null: false                    |
| price       | integer     | null: false                    |
| user        | references  | null: false, foreign_key: true |

### Association 

- has_one :buying
- belongs_to :user

## buys テーブル

| Column      | Type        | Options                        |
| ----------- | ----------- | ------------------------------ |
| user        | references  | null: false, foreign_key: true |
| item        | references  | null: false, foreign_key: true |

### Association 

- belongs_to :user
- belongs_to :item
- has_one :shipping_address

## shipping_addresses テーブル

| Column        | Type        | Options                        |
| ------------- | ----------- | ------------------------------ |
| post_code     | string      | null: false                    |
| area_id       | integer     | null: false                    |
| city          | string      | null: false                    |
| address       | string      | null: false                    |
| building_name | string      |                                |
| phone_number  | string      | null: false                    |
| buys          | references  | null: false, foreign_key: true |

### Association 

- belongs_to :buy

