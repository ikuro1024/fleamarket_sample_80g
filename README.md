# README

# users(ユーザー) テーブル
|Column|Type|Option|
|------|----|------|
|nickname|string|null: false|
|email|string|null: false unique: true|
|password|string|null: false|

## Association
has_many :products
has_one :profile

# profiles(本人情報) テーブル
|Column|Type|Option|
|------|----|------|
|first_name|string|null: false|
|last_name|string|null: false|
|first_name_kana|string|null: false|
|last_name_kana|string|null: false|
|birth_year|string|null: false|
|birth_month|string|null: false|
|birth_day|string|null: false|
|phone_number|string||
|zip_code|string|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|address|string|null: false|
|building|string||
|user_id|integer|foreign_key|

## Association
belongs_to :user

# products(商品) テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|
|price|string|null: false|
|detail|text|null: false|
|category_id|integer|foreign_key|
|bland_id|integer|foreign_key|
|size_id|integer|foreign_key|
|state_id|integer|foreign_key|
|user_id|integer|foreign_key|
|condition_id|integer|foreign_key|

## Association
has_many :images
has_many :state
has_many :condition
belongs_to :category
belongs_to :brand

# images(商品イメージ) テーブル
|Column|Type|Option|
|------|----|------|
|url|text|null: false|
|product_id|integer|foreign_key|

## Association
belongs_to :product

# cards(クレジットカード) テーブル
|Column|Type|Option|
|------|----|------|
|user_id|integer|null: false|
|token|||

## Association
belongs_to :user

# sizes(サイズ) テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|

## Association
belongs_to :product

# orders(注文情報) テーブル
|Column|Type|Option|
|------|----|------|
|product_id|integer|foreign_key null:false|

## Association
belongs_to :user

# conditions(商品状態) テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|

## Association
belongs_to :product

# states テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|

## Association
belongs_to :product

# categories(大元のカテゴリー) テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|

## Association
has_many :products
has_many :category_parents
has_many :category_childs

# category_parents(親カテゴリー) テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|
|category_id|integer|foreign_key|

## Association
belongs_to :category
has_many :category_childs

# category_childs(子カテゴリー) テーブル
|Column|Type|Option|
|------|----|------|
|name|string|null: false|
|category_id|integer|foreign_key|
|category_parent_id|integer|foreign_key|

## Association
belongs_to :categories
belongs_to :categories_parent

# shippings(発送) テーブル
|Column|Type|Option|
|------|----|------|
|method|integer|null: false|
|prefecture_from|integer|null: false|
|period_before_shipping|string|nul: false|
|fee_burden|boolean|null: false|

## Association
has_many :products

# brand(ブランド) テーブル
|Column|Type|Option|
|------|----|------|
|name|string||
|brand_group|integer|foreign_key|

## Association
has_many :products
