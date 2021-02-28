# テーブル設計

## users テーブル

| Column               | Type    | Options     |
| -------------------- | ------- | ------------|
| nickname             | string  | null: false |
| email                | string  | null: false |
| password             | string  | null: false |
| encrypted_password   | string  | null: false |
| family_name          | string  | null: false |
| first_name           | string  | null: false |
| family_name_kana     | string  | null: false |
| first_name_kana      | string  | null: false |
| birth_day            | date    | null: false |

### Association 

- has_many :items
- has_many :buyings

## items テーブル

| Column      | Type        | Options                        |
| ----------- | ----------- | ------------------------------ |
| image       | string      | null: false                    |
| name        | string      | null: false                    |
| description | string      | null: false                    |
| category    | string      | null: false                    |
| status      | string      | null: false                    |
| cost        | string      | null: false                    |
| area        | string      | null: false                    |
| days        | string      | null: false                    |
| price       | string      | null: false                    |
| user_id     | references  | null: false, foreign_key: true |

### Association 

- has_one :buyings
- belongs_to :users

## buyings テーブル

| Column      | Type        | Options                        |
| ----------- | ----------- | ------------------------------ |
| user_id     | references  | null: false, foreign_key: true |
| items_id    | references  | null: false, foreign_key: true |

### Association 

- belongs_to :users
- belongs_to :items
- has one :shipping_addresses

## shipping_addresses テーブル

| Column        | Type        | Options                        |
| ------------- | ----------- | ------------------------------ |
| post_code     | string      | null: false                    |
| prefecture    | string      | null: false                    |
| city          | string      | null: false                    |
| address       | string      | null: false                    |
| building_name | string      | null: false                    |
| phone_number  | string      | null: false                    |
| buyings_id    | references  | null: false, foreign_key: true |

### Association 

- belongs_to :buyings

