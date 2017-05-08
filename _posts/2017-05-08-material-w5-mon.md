---
title: "5주차 수업자료 (devise)"
tag: material
author: "우미연"
---

이 수업자료는 기존 프로젝트를 기반으로 `devise` 젬를 추가하는 내용입니다. (프로젝트 구조는 3주차 CRUD 보조자료와 같습니다.)

### Devise
여러가지 이유(보안 등)로 개발자가 직접 회원관리 시스템을 구현하기 쉽지 않은데, `devise`를 사용하면  쉽게 회원관리가 가능하다.

- [devise github](https://github.com/plataformatec/devise)

# Devise 사용하기
- `Gemfile`에 `devise`젬 추가후 `bundle install`을 실행한다.

```ruby
#Gemfile
gem 'devise'
```


- 다음 명령어를 사용하여 `devise`로 user모델을 생성할수 있다.

```sh
$ rails g devise:install
$ rails g devise user
```

`rails g devise:install` 이후 나오는 4개의 과정을 시키는대로 해준다.(하라는대로만 하면된다.)

4번의 `rails generate devise:views` 는 view를 생성해주는데 나중에 해도 관계없다.


- 모델간의 관계를 설정해준다.(하나의 `user`가 다수의 `post`를 작성할수 있다고 가정.)

```ruby
# devise 젬을 통해 생성된 user.rb
devise :database_authenticatable, :registerable,
       :recoverable, :rememberable, :trackable, :validatable

has_many :posts #이부분만 추가해준다.
```


```ruby
# post.rb
belongs_to :user
```


작성이 끝나면 `rake db:migrate` 명렁어를 실행한다.



```ruby
# routes.rb
Rails.application.routes.draw do
  devise_for :users
  # For details on the DSL available within this file, see http://guides.rubyonrails.org/routing.html
  resources :posts
  root "posts#index"
end
```


- **CRUD**에 권한을 부여한다.(index, showㄴ)

```ruby
# posts_controller.rb
class PostsController < ApplicationController
  before_action :authenticate_user!, except: [ :index, :show ]

...

```

- 필요한 위치에 로그인 및 회원가입 페이지로 이동하는 링크를 달아준다.
- 이때 `devise`에서 제공하는 `current_user`라는 변수를 이용하거나, `user_signed_in?`(로그인 되어있는 상태)를 이용하여 사용자가 로그인한 상태인지 확인하고 다른 ui를 적용할 수 있다.

```erb
<% if user_signed_in? %>
    <%= link_to '로그아웃', destroy_user_session_path, method: :delete, data: { confirm: "Are you sure?" } %>
<% else %>
    <%= link_to '로그인', new_user_session_path %>
    <%= link_to '회원가입', new_user_registration_path%>
<% end %>
```

## Author

written by [우미연](https://miyon2.github.io).

![](https://avatars.githubusercontent.com/miyon2?v=2&s=100)

<a href="https://miyon2.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>