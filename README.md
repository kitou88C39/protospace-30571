# テーブル設計

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| email    | string | null: false |
| password | string | null: false |
| name     | string | null: false |
| profile  | text   | null: false |
|occupation| text   | null: false |
| position | text   | null: false |
### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## comments テーブル

| Column    | Type      | Options     |
| ------    | ------    | ----------- |
| text      | text      | null: false |
| user      |references |             |
| prototype |references |             |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages


## prototypes テーブル

| Column     | Type          | Options     |
| ------     | ----------    | ----------- |
| title      | string        | null: false |
| catch_copy | text          | null: false |
| concept    | text          | null: false |
| image      | AcitveStorage |             |
| user       | referrences   |             |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user
