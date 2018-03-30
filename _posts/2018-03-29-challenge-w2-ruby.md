---
title: "2주차 첼린지 : 현경이의 성적표"
tag: challenge
author: "이현경"
winner: ""
mvp: ""
---

* 현경이의 성적을 입력하고 재수강이 필요한과목, 우수한과목, 평점과 학사경고/장학금 여부를 알아보자.

#### 상세설명

```
한 학기가 끝난 지금 현경이의 성적을 알아보자!
현경이는 이번에 6개의 전공 수업을 들었다. (6개의 수업 성적을 직접 입력받아보자.)
각 학점의 점수는 Hash에 저장하여라.
("A+": 4.5 "A": 4.0 "B+": 3.5 "B": 3.0 "C+": 2.5 "C": 2.0 "D": 1.0 "F": 0)
현경이의 6개의 과목 성적 중 재수강이 필요한 과목(C+이하)과 우수한 과목(A이상)의 수를 출력해보자.
평점을 구하는 함수를 구현해서 출력해보자.
그리고 현경이의 평점과 현경이의 평점이 학사경고(2.0)인지, 성적장학금(4.0)을 받을 수 있는지 출력해보자.
```
#### 유의사항
- 해시, 반복문, 메소드, 조건문을 이용해서 작성하세요.

#### 코드

```rb
=begin

한 학기가 끝난 지금 현경이의 성적을 알아보자!
현경이는 이번에 6개의 전공 수업을 들었다. (6개의 수업 성적을 직접 입력받아보자.)
각 학점의 점수는 Hash에 저장하여라.
("A+": 4.5 "A": 4.0 "B+": 3.5 "B": 3.0 "C+": 2.5 "C": 2.0 "D": 1.0 "F": 0)

현경이의 6개의 과목 성적 중 재수강이 필요한 과목(C+이하)과 우수한 과목(A이상)의 수를 출력해보자.
평점을 구하는 함수를 구현해서 출력해보자.
그리고 현경이의 평점과 현경이의 평점이 학사경고(2.0)인지, 성적장학금(4.0)을 받을 수 있는지 출력해보자.

=end
score = {
	"A+" => 4.5,
	"A" => 4.0,
	"B+" => 3.5,
	"B" => 3.0,
	"C+" => 2.5,
	"C" => 2.0,
	"D" => 1.0,
	"F" => 0
}

score = []
for i in 1..6
	print "현경이의 #{i}번째 과목 성적을 입력하세요:  "
	score.push(score[gets.chomp.upcase])
end

print score
puts ""

#우수한 과목, 재수강이 필요한과목
count = [0,0]

score.each do |a|
	if a >= 4.0
		count[0]+=1
	elsif a <= 2.5
		count[1]+=1
	end
end

def avg(input_arr)
	sum = 0

	input_arr.each do |a|
		sum += a
	end

	return sum/input_arr.length
end

puts "현경이의 재수강 과목의 수는 #{count[1]}개 , 우수한 과목의 수는 #{count[0]}개 입니다."
puts "현경이의 평점은 #{avg(score)}입니다."

if avg(score) >= 4.0
	puts "성적장학금을 받을 수 있습니다!!!우와아아"
elsif avg(score) < 2.0
	puts "학사경고입니다. 분발하세요"
end
```

## Author

written by [이현경](https://hyunkyung12.github.io).

<a href="https://hyunkyung12.github.io" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github Page &rarr;</a>
