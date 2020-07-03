# README
# chat-space DB設計
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|name|string|null: false、index: true|
### Association
- has_many :messages
- has_many :members
- has_many  :groups,  through:  :members


## Groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users, through: :members
- has_many :members

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|
|image|string|
|group|references|null: false, foreign_key: true|
|user|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

