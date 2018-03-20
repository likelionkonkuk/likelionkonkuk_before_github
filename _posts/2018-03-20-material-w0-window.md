---
title: "0주차 보조자료(Vagrant)"
tag: material
author: "건대멋사"
---

### windows를 탈출하자! (vagrant 설치)

## versions / install

* [virtualBox](https://download.virtualbox.org/virtualbox/5.1.30/) : 5.1.30

![virtualbox]({{ site.url }}/assets/material/vagrant/1.png)


* [Vagrant](https://releases.hashicorp.com/vagrant/?_ga=2.237010176.1475687836.1513147132-756484628.1513147132) : 1.9.5

![vagrant]({{ site.url }}/assets/material/vagrant/2.png)![git]({{ site.url }}/assets/material/vagrant/3.png)

* [git for windows](https://git-for-windows.github.io/) - git bash

- *모든 설치는 default로*
- atom이나 sublime과 같은 text-editor도 설치하기

#### setting - vagrant

1. Windows에서 폴더 하나를 만든다. (vagrant 가상 환경과 windows와 공유하는 폴더가 될 예정임.)![folder]({{ site.url }}/assets/material/vagrant/4.png)
2. 해당 폴더의 경로에서 git bash 창을 연다.![gitbash]({{ site.url }}/assets/material/vagrant/5.png)![vagrant here]({{ site.url }}/assets/material/vagrant/6.png)

```console
$ vagrant init
```

3. Vagrantfile이 생겼을텐데, 이를 수정하고 저장한다.![vagrant init]({{ site.url }}/assets/material/vagrant/7.png)![vagrantfile](./8.png)![vagrantfile]({{ site.url }}/assets/material/vagrant/9.png)

```
# 다음 내용으로 수정
Vagrant::DEFAULT_SERVER_URL.replace("https://vagrantcloud.com")
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 4567, host: 4567
end
```

4. 가상 환경을 만든다.![vagrant up]({{ site.url }}/assets/material/vagrant/10.png) ![result]({{ site.url }}/assets/material/vagrant/11.png)

```console
$ vagrant up
```

5. 가상환경에 접속한다.![vagrant ssh]({{ site.url }}/assets/material/vagrant/12.png)

```console
$ vagrant ssh
```

6. 가상머신에 접속된 상태에서 공유폴더에 접근한다.![vagrant ssh]({{ site.url }}/assets/material/vagrant/13.png)

```console
$ cd /vagrant
```

## setting - vagrant 내 루비 개발 환경

> 루비버전은 2.4.0으로 맞춘다.

**아래의 코드들은 반드시 가상 환경 내에서 입력해야합니다.**
git bash 창에서 `ubuntu@ubuntu-xenial:~$` 확인!

```console
$ vagrant ssh
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-103-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.


Last login: Wed Dec 13 07:26:42 2017 from 10.0.2.2
ubuntu@ubuntu-xenial:~$

```

1. 아래의 코드를 git bash 창에 복붙한다. **반드시 vagrant 환경 내에서**

```console
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev nodejs yarn
```

2. 한번 더 한땀한땀.. git bash 창에..

```console
cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 2.4.0
rbenv global 2.4.0
ruby -v
```


3. 한번 더! git bash 창에..

```console
gem install bundler
rbenv rehash
```

추가적으로, git 설정을 vagrant 환경에서 다시 해줘야합니다.

```console
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR@EMAIL.com"
```

4. 레일즈 설치하기!
```console
gem install rails -v 5.0.6
rbenv rehash
```

5. 버전 확인하기
```console
ruby -v 
# 2.4.0
rails -v 
# 5.0.6
```

---

## Author

written by [건대멋사](likelionkonkuk.github.io).

![](https://avatars.githubusercontent.com/likelionkonkuk?v=2&s=100)

<a href="https://github.com/likelionkonkuk" target="_blank" class="btn btn-black"><i class="fa fa-github fa-lg"></i> Visit on Github &rarr;</a>