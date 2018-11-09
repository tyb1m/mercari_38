# README

## brands

|Column|Type|Options|
|------|----|-------|
|brand_name|text|add_index|
|category_l_id|integer|null: false|

### Association
- belongs_to :item

## items

|Column|Type|Options|
|------|----|-------|
|name|string|null:false,add_index|
|price|integer|null:false|
|condition|string|null:false|
|description|text|null: false|
|status|integer|null: false|
|shipping_fee|integer|null: false|
|arrive_date|integer|null: false|
|like_count|integer|null: false|
|category_s_id|integer|null: false|
|category_m_id|integer|null: false|
|category_l_id|integer|null: false|


### Association
- belongs_to :user
- has_many : likes, dependent: :destroy
- has_many : images, dependent: :destroy
- belongs_to : category_s
- belongs_to : category_m
- belongs_to : category_l
- has_one : deal
- belongs_to : brand
- belongs_to : sizes

## users

|Column|Type|Options|
|------|----|-------|
|nickname|string||
|email|reference|null:false,unique: true|
|password|string|null:false|
|profile|text||
|phone_number|string|null:false,unique: true|
|first_name|string|null:false|
|last_name|string|null:false|
|address|string|null:false|
|birthday|string|null:false|

### Association
- has_many : items, dependent: :destroy
- has_many : likes, dependent: :destroy
- has_many : deals
- has_many : comments

## deals

|Column|Type|Options|
|------|----|-------|
|item_id|reference|null: false,foreign_key: true|
|dealt_at|datetime|null: false|

### Association
- belongs_to :item
- belongs_to :user
- has_many : deal_messages, dependent: :destroy

## likes

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item

## images

|Column|Type|Options|
|------|----|-------|
|image_url|string|null: false|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :item

## comments

|Column|Type|Options|
|------|----|-------|
|comment|string|null:false|
|item_id|reference|null: false, foreign_key: true|
|user_id|reference|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :item

## category_s

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|category_m_id|reference|null: false, foreign_key: true|

### Association
- belongs_to :category_m
- has_many :items

## category_m

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|category_l_id|reference|null: false, foreign_key: true|

### Association
- has_many :category_s
- belongs_to :category_l
- has_many :items

## category_l

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :catecory_m
- has_many :items

##sizes

|Column|Type|Options|
|------|----|-------|
|category_s_id|string|null: false|
|name|string|-------|

### Association
- belongs_to :category_s
- has_many :items

##deal_messages

|Column|Type|Options|
|------|----|-------|
|messages|string|null: false|
|deal_id|string|null: false|
|user_id|string|null: false|

### Association
- belongs_to : deal
