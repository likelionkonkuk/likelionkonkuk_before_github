---
title: "3주차 첼린지 : 로또"
tag: challenge
author: "정다혜"
winner: "김범식"
mvp: "김범식"
---


로또 번호 추천 프로그램을 만들어보자.
로또 api를 이용해 이번 주 당첨정보를 받아와 비교해보자.


[API 보조자료](http://konkuk.likelion.org/material-w3-api)(api에 관련된 부분의 코드는 이미 적혀있습니다.)

1~45까지의 숫자 중 6개를 랜덤으로 뽑아 이번주 당첨번호와 비교하는 프로그램을 만들어주세요!

1. `config/routes.rb`에서 root경로 지정해주기
2. `app/controllers/lotto_controller.rb` 에 코드 추가하기
3. `app/views/lotto/index.html.erb`, `app/views/lotto/pick_and_check.html.erb` 코드 추가

---

#### 코드

```ruby
require ('open-uri')        # 웹 페이지 open 에 필요.
require ('json')            # JSON을 Hash로 변환하는데 필요.

class LottoController < ApplicationController
  def index
  end

  def pick_and_check
  	# page에 해당 웹 페이지를 열어서 저장. 
  	# page = open('http://www.nlotto.co.kr/common.do?method=getLottoNumber&drwNo=') 

  	# lotto_info 에 page 내용 (JSON 형식의 data) 을 읽어서 저장.
  	# lotto_info = page.read  

  	# lotto_hash 에 JSON 형식인 lotto_info 를 Hash 로 파싱(변환)하여 저장.
  	# lotto_hash = JSON.parse(lotto_info)    

  	# puts lotto_hash    #=> JSON 데이터가 Hash 로 변환되어 출력.

  	# 위의 주석된 코드들을 1줄로 줄인 코드! get_info에 hash가 저장되어있음.
  	get_info = JSON.parse open('http://www.nlotto.co.kr/common.do?method=getLottoNumber&drwNo=').read

  	drw_numbers = []		# 이번주 당첨번호
    get_info.each do |k, v|
       drw_numbers << v if k.include? 'drwtNo'
    end
    drw_numbers.sort!
    bonus_number = get_info["bnusNo"]		#보너스번호
 
    # 여기서 부터 코드를 작성해 주세요. 로또 번호 6개 랜덤생성 후 정렬.
    # 이번주 당첨번호와 비교해서 1등부터 6등까지의 결과를 출력해내세요.

    rand_numbers = [*(1..45)].sample(6)

    count = drw_numbers & rand_numbers

    result = ""

    if count.count == 6
      result = 1
    elsif count.count == 5 && rand_numbers.include?(bonus_number)
      result =2
    elsif count.count == 5
      result = 3
    elsif count.count == 4
      result = 4
    elsif count.count == 3
      result = 5
    else
      result = 6
    end


    # 인스턴스에 변수를 저장해주세요!
    @drw_numbers = drw_numbers
    @bonus_number = bonus_number

    # 추가생성한 변수들 인스턴스로 지정.

    @rand_numbers = rand_numbers
    @count = count
    @result = result
  end
end
```

```erb
<div class="container">
  <h1>추첨 결과를 보여줄 view 입니다.</h1>
  <p><%= "이번주 로또 번호는 #{@drw_numbers} 이고, 보너스 번호는 #{@bonus_number} 입니다." %></p>
	<!-- 밑에 추첨한 로또 번호, 겹치는 번호, 결과를 출력해주세요.-->
	<p><%= "생성된 로또 번호는 #{@rand_numbers} 입니다." %></p>
	<p><%= "겹치는 번호는 #{@count} 입니다." %></p>
	<p><%= "결과는 #{@result}등 입니다."%></p>
</div>
```

---


#### 다운로드

- [로또 첼린지](https://github.com/likelionkonkuk/w3_challenge_6th)

- `git`을 사용하거나 `zip`파일로 다운받아 설치합니다.
```
git clone https://github.com/likelionkonkuk/w3_challenge_6th.git
```

#### 유의사항
- json에 대한 설명은 주석으로 되어있으므로 읽고 해주세요.


## Author

written by [정다혜](https://dh00023.github.io).

![](https://avatars.githubusercontent.com/dh00023?v=2&s=100)

<a href="https://dh00023.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>