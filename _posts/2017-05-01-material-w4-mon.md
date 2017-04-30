---
title: "4주차 월요일 수업자료 (Paperclip & 모의 아이디어톤)"
tag: material
author: "천민우"
---

**Paperclip**이란? ([링크](https://github.com/thoughtbot/paperclip))

쉽게 웹사이트에 사진을 업로드 할 수 있도록 도와주는 `gem`. 비슷한 잼으로는 `carrierwave`가 있다. 

### 설치방법

- `imageMagick`을 설치한다.

```sh
#ubuntu
sudo apt-get install imagemagick

#mac os
brew install imagemagick
```

- `Gemfile`에 `paperclip` 젬을 추가한뒤, `bundle install`.

```rb
gem "paperclip"
```

- `paperclip`을 통해 이미지를 추가할 `model`과 관계설정 및 `db`생성(title, description등이 있는 post모델이 있다고 가정.)

```sh
#post 모델에 image라는 이미지를 추가하고 싶은경우
rails generate paperclip post image
```

```rb
class Post < ActiveRecord::Base
  has_attached_file :image, styles: { medium: "300x300>", thumb: "100x100>" }
  validates_attachment_content_type :image, content_type: /\Aimage\/.*\z/
end
```

- controller에 image를 저장수정 할수 있도록 코드를 추가한다.

```rb
#posts_controller.rb

private

def post_params
  params.require(:post).permit(
    :title, 
    :description, 
    :image)
end
```

- `_form.html.erb`에 이미지를 업로드 할수있도록 `form`태그를 수정

```erb
<%= form_for @post, html: { multipart: true } do |f| %>
  <%= f.text_field :title %>
  <%= f.text_area :description %>
  <%= f.file_field :image %>
<% end %>
```


-`show.html.erb`에서 업로드한 이미지 불러오기

```erb
<%= @post.title%>
<%= @post.description%>
<%= image_tag @post.avatar.url %>
```


---

### 참고자료
- [paperclip](https://github.com/thoughtbot/paperclip)
- [imagemagick](http://www.imagemagick.org/script/index.php)

---

## Author

written by [천민우](https://project42da.github.io).

![](https://avatars.githubusercontent.com/project42da?v=2&s=100)

<a href="https://project42da.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>
