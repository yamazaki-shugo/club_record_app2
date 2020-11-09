# テーブル設計

## users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| position_id        | integer| null: false |


### Association

- has_many :messages
- has_many :events
- has_many :room_users
- has_many :rooms, through: :room_users

## rooms テーブル

| Column             | Type       | Options           |
| ------------------ | ---------- | ----------------- |
| team_name          | string     | null: false       |
| password_digest    | string     | null: false       |

### Association

- has_many :messages
- has_many :events
- has_many :room_users
- has_many :users, through: :room_users


## room_users テーブル

| Column             | Type       | Options           |
| ------------------ | ---------- | ----------------- |
| room               | references | foreign_key: true |
| user               | text       | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :room

## messages テーブル

| Column             | Type       | Options           |
| ------------------ | ---------- | ----------------- |
| content            | text       | null: false       |
| room               | references | foreign_key: true |
| user               | references | foreign_key: true |


### Association

belongs_to :user
belongs_to :room

## events テーブル

| Column             | Type       | Options           |
| ------------------ | ---------- | ----------------- |
| title              | string     | null: false       |
| content            | text       | null: false       |
| start_time         | datetime   | null: false       |
| user               | references | foreign_key: true |
| room               | references | foreign_key: true |

### Association

- belongs_to :user
- belongs_to :room
