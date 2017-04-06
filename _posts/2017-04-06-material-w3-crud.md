---
title: "3주차 보조자료(CRUD)"
tag: material
author: "정다혜"
---

#### 1. 애플리캐이션 생성

```
rails new crud
```

#### 2. posts controller 생성

```
rails g controller posts
```

#### 3. post 모델생성

```
rails g model post title content:text
rake db:migrate
```

#### 4. RESTful한 라우팅 설정

```ruby
#routes.rb
Rails.application.routes.draw do
  resources :posts
  root "posts#index"
end
```

#### 5. index액션(Post 모델에 저장된 모든 요소 목록 출력)

```erb
<!--index.html.erb-->
<h2>Lists</h2>
<% @posts.each do |post| %>
	<h2><%= link_to post.title, post %></h2>
<% end %>
<%= link_to "new post", new_post_path %> 
```

```ruby
#post_controller.rb
class PostsController < ApplicationController
  def index
  	@posts = Post.all.order("created_at DESC")
  end
end
```

#### 6. Reading 보여지는 페이지 만들기 (show)

```ruby
#post_controller.rb
class PostsController < ApplicationController
  before_action :find_posts, only: [:show, :edit, :update, :destroy]
  def index
  	@posts = Post.all.order("created_at DESC")
  end

  def show
  end

  private

  def find_posts
  	@post = Post.find(params[:id])
  end
end
```

```erb
<!--show.html.erb-->
<h2>Title : <%= @post.title %> </h2>
<p> Content : <%= @post.content %></p>

<%= link_to "Home" ,root_path %>
<%= link_to "edit post" , edit_post_path %>
<%= link_to "delete post" , post_path(@post), method: :delete, data: {confirm: "Are you sure?"} %>
```

##### 7. 게시글 작성페이지(create, new)만들기

```ruby
#post_controller.rb
class PostsController < ApplicationController

  def new
  	@post = Post.new
  end

  def create
  	@post = Post.new(post_params)

  	if @post.save
  		redirect_to @post
  	else
  		render 'new'
  	end  	
  end

  private

  def post_params  	
  	params.require(:post).permit(:title, :content)
  end
end
```

```erb
<!--_form.html.erb-->
<%= form_for @post do |f| %>
  <div class="field">
    <%= f.label :title %>
    <%= f.text_field :title %>
  </div>
  <div class="field">
    <%= f.label :content %>
    <%= f.text_field :content %>
  </div>
  <div class="actions">
    <%= f.button :submit %>
  </div>
<% end %>
```

```erb
<!--new.html.erb-->
<%#아래에 복-붙! %>
<h2>New Posts</h2>

<%= render 'form' %>

<%= link_to "Back", posts_path %>
```

#### 8. 수정페이지(edit, update)만들기


```ruby
#post_controller.rb
class PostsController < ApplicationController
  before_action :find_posts, only: [:show, :edit, :update, :destroy]

  def edit
  end

  def update
  	if @post.update(post_params)
  		redirect_to @post
  	else
  		render 'edit'
  	end
  end

  private

  def post_params  	
  	params.require(:post).permit(:title, :content)
  end

  def find_posts  	
  	@post = Post.find(params[:id])
  end
end
```

```erb
<!--_form.html.erb-->
<%= form_for @post do |f| %>
  <div class="field">
    <%= f.label :title %>
    <%= f.text_field :title %>
  </div>
  <div class="field">
    <%= f.label :content %>
    <%= f.text_field :content %>
  </div>
  <div class="actions">
    <%= f.button :submit %>
  </div>
<% end %>
```

```erb
<!-- edit.html.erb -->
<%#아래에 복-붙! %>
<h2>Edit Post</h2>

<%= render 'form' %>

<%= link_to "Back", posts_path %>
```


#### 9. 삭제(destroy)

```ruby
#post_controller.rb
class PostsController < ApplicationController
  before_action :find_posts, only: [:show, :edit, :update, :destroy]

  def destroy
  	@post.destroy
  	redirect_to posts_path
  end

  private

  def find_posts  	
  	@post = Post.find(params[:id])
  end
end
```


## Author

written by [정다혜](https://dh00023.github.io).

![](https://avatars.githubusercontent.com/dh00023?v=2&s=100)

<a href="https://dh00023.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>