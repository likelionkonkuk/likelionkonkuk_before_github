---
title: "5주차 수요일 수업자료 (1:N, M:N)"
tag: material
author: "천민우"
---

## Goals

- Learn how to use 1:N, M:N in model.
- Use Faker gem with task to fill database.
- Learn validation in models.

## Structure

#### User Model
|id|email|age|created_at|updated_at|
|---|---|---|---|---|
|integer|string|integer|datetime|datetime|

*has_many posts, has_many comments, has_and_belongs_to_many group*

#### Post Model
|id|title|content|user_id|created_at|updated_at|
|---|---|---|---|---|---|
|integer|string|text|integer|datetime|datetime|

*belongs_to user, has_many comments*

#### Comment Model
|id|content|post_id|user_id|created_at|updated_at|
|---|---|---|---|---|---|
|integer|string|integer|integer|datetime|datetime|

*belongs_to user, belongs_to post*

#### Group Model
|id|name|created_at|updated_at|
|---|---|---|---|
|integer|string|datetime|datetime|

*has_and_belongs_to_many user*


## Getting Started

### 0. Install Gems

```rb
gem 'faker'
```

### 1. Use 1:N (User, Posts , Comments)

#### Make User Model

`rails g model user name email age:integer`

#### Make Post Model

`rails g model post title content user:references`

#### Make Comment Model

`rails g model comment content user:references post:references`


### 2. Use M:N (Users & Groups)

#### Make Group Model

`rails g model group name`

#### Make `has_and_belongs_to_many` association

`rails g migration CreateJoinTableGroupUser group user`

#### Declare the `has_and_belongs_to_many` in the user ,group model

```rb
class Group < ApplicationRecord
  has_and_belongs_to_many :users
end
```


```rb
class User < ApplicationRecord
  has_and_belongs_to_many :groups
end
```

----

### User Task

Make `db.rake` in `lib/tasks/` directory

```rb
namespace :db do

	desc "populates th database with user"

	task old: :environment do
		5.times do
			User.create!(
				name:Faker::Name.name,
				age:Faker::Number.between(40, 50),
				email:Faker::Internet.email,
				group_ids:1
			)
		end
	end

	task young: :environment do
		5.times do
			User.create!(
				name:Faker::Name.name,
				age:Faker::Number.between(20, 30),
				email:Faker::Internet.email,
				group_ids:2
			)
		end
	end

	task oldcomment: :environment do
		(1..5).each do |i|
			Comment.create!(
				content:Faker::Lorem.sentence,
				post_id:1,
				user_id:i
			)
		end
	end
end
```


### Models Validates

#### app/models/user.rb

```ruby
class User < ApplicationRecord
	has_and_belongs_to_many :groups
	has_many :posts
	has_many :comments

	def name=(s)
    super s.titleize
	end
	
	RegExp = /\A([\w+\-].?)+@[a-z\d\-]+(\.[a-z]+)*\.[a-z]+\z/i

	validates :name, length: {maximum: 100}, presence: true
	validates :age, numericality: {only_integer: true, greater_than: 19, less_than:30}, presence: true
	validates :email, format: {with: RegExp}, uniqueness: {case_sensitive: false}, presence: true
end
```

--------------------------------

#### app/models/group.rb

```ruby
class Group < ApplicationRecord
	has_and_belongs_to_many :users

	validates :name, length: {maximum: 20}, uniqueness: true, presence: true
end
```


--------------------------------

#### app/models/post.rb

```ruby
class Post < ApplicationRecord
  belongs_to :user
  has_many :comments

  words = ["shit", "fuck", "hell"]
  
  before_save{ 
  	words.each do |word| 
  		len = word.length
  		self.content.gsub!(/#{word}/, '*'*len) if(self.content.include?(word))
  	end
  }

  validates :title, length: {minimum: 2 , maximum: 30}, presence: true
	validates :content, presence: true
end
```

--------------------------------

#### app/models/comment.rb

```ruby
class Comment < ApplicationRecord
  belongs_to :user
  belongs_to :post

	words = ["shit", "fuck", "hell"]
  
  before_save{ 
  	words.each do |word| 
  		len = word.length
  		self.content.gsub!(/#{word}/, '*'*len) if(self.content.include?(word))
  	end
  }
	
	validates :content, length: {maximum: 200}, presence: true
end
```



---

### 참고자료
- [Rails Active Record](http://guides.rubyonrails.org/association_basics.html)
- [Faker](https://github.com/stympy/faker)


---

## Author

written by [천민우](https://project42da.github.io).

![](https://avatars.githubusercontent.com/project42da?v=2&s=100)

<a href="https://project42da.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>
