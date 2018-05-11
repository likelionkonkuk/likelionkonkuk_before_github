---
title: "5주차 강의자료"
tag: material
author: "이현경"
---


# W5 강의내용 정리

## 1. CRUD 복습

``posts.controller.erb``

```ruby
class PostsController < ApplicationController

  def create
    post = Post.new
    post.title = params[:post_title]
    post.content = params[:post_content]
    post.save
    
    redirect_to '/'
  end

  def new
    @post = Post.new
  end

  def index
    @posts = Post.all
  end

  def show
    @post = Post.find(params[:post_id])
  end

  def update
    post = Post.find(params[:post_id])
    post.title = params[:post_title]
    post.content = params[:post_content]
    post.save
    
    redirect_to '/'
  end

  def edit
    @post = Post.find(params[:post_id])
  end

  def destroy
    post = Post.find(params[:post_id])
    post.destroy
    
    redirect_to '/'
  end
end
```

```
post_title, post_content : view의 <form> name 속성으로 받은 값
post_id : route의 :post_id 에서 받은 값
```

## 2. link_to

route에서 설정한 별명으로 url 설정이 가능


``routes.rb``
```ruby
get 'posts/show/:post_id' => 'posts#show', as: post
```

``index.html.erb``

```ruby
<%= link_to '[상세보기]', post_path(post_id: p.id) %>
```

**get 'posts/show/:post_id' 'posts#show'** 라는 라우팅을 post 라는 별명을 붙여 사용하겠다

## 3. form_helper

- CSRF 공격 방지 태그 기본 제공
- 기본 method 는 POST

#### 1. form_tag

기본 구성
```
<%= form_tag(“어디로”, method: “어떻게”) do %>
	내용
<% end %>
```

``new.html.erb``
```ruby
<%= form_tag(posts_path, method: "post") do %>
    <%= label_tag 'post_title', '제목' %>
    <%= text_field_tag 'post_title', nil, placeholder: '제목을 입력하세요' %><br>

    <%= label_tag 'post_content', '내용' %>
    <%= text_area_tag 'post_content', nil, placeholder: '내용을 입력하세요' %>

    <%= submit_tag 'submit' %>
<% end %>
```

form_tag의 속성 값들은 
https://apidock.com/rails/ActionView/Helpers/FormTagHelper 를 참고하세요


#### 2. form_for

기본 구성
```
<%= form_for(무엇을, url: 어디로, method: ‘어떻게’) do | f |%>
	내용
<% end %>

```
- RESTful 한 라우팅 설정이 되어있다면 url, method 는 생략해도 rails 가 알아서 찾아줌

``new.html.erb``
```ruby
<%= form_for(@post, url: post_path, method: 'post') do |f| %>
    <%= f.text_field :title %>
    <%= f.text_area :content %>
    <%= f.submit '제출' %>    
<% end %>
```

모델속성을 접근하기 때문에 반드시 column 이름과 같게 보내주어야 함

```
- params[:post_title] (X)
- params[:post][:title] (O)
```

``posts.controller.rb``
```ruby
def create
  post = Post.new
  post.title = params[:post][:title]
  post.content = params[:post][:content]
  post.save
   
  redirect_to '/'
end

```

form_for의 속성 값들은 
https://apidock.com/rails/ActionView/Helpers/FormHelper/form_for 를 참고하세요

## 4. controller 코드 정리하기

#### 1. before_action

``posts.controller.erb`` 에서 중복되는 ``@post = Post.find(parmas[:post_id])`` 정리
```ruby
private
  
def set_post
  @post = Post.find(params[:id])
end
```
정의 후, controller 상단에

```ruby
before_action :set_post, only: [:show, :edit, :update, :destroy]
```

- 의미 : show, edit, update, destroy action 실행 전에 set_post 를 실행해라
- show, edit, update, destroy 에서 set_post 에 해당하는 코드는 지우면 됨

#### 2. strong_parameter

```ruby
private

def post_params
  params.require(:post).permit(:title, :content)
end

```
정의 후, 액션을 고침
```ruby
def create   
  post = Post.new(post_params)
  post.save
    
  redirect_to '/'
end

def update
  @post.update(post_params)
  @post.save
    
  redirect_to '/'
end
```

#### 3. form_render

RESTful 한 라우팅 설정 후 form_tag에서 url, method 를 지울 수 있고, 
그러면 new, edit 의 form 이 동일해짐

``_form.html.erb`` 생성 후 form 을 넣어줌
```ruby
<%= form_for(@post) do |f| %>
    <%= f.text_field :title %>
    <%= f.text_area :content %>
    <%= f.submit '제출' %>    
<% end %>
```
그리고 form 이 들어갈 자리에 render 코드를 넣어줌
```ruby
<%= render 'form' %>
```

- 의미 : ```form 이 들어갈 자리에 ``_form.html.erb`` 의 내용을 넣겠다

## 5. RESTful

라우팅을 좀 더 편하게 하도록 도와줌

``routes.rb``

```ruby
root 'posts#index'
resources :posts
```

``rake routes`` 를 쳐보면 자동으로 route들이 생성된 것을 볼 수 있음

[강의자료 받기](https://github.com/likelionkonkuk/w5_material)

## Author

written by [이현경](https://hyunkyung12.github.io).

<a href="https://hyunkyung12.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>