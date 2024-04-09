# Mac-Ruby-Install

Mac OS 에 최신 루비를 설치하는 방법을 적은 레포입니다

Brew를 사용하지 않으며 rbenv 와 ruby-build 레포를 참조하여 만들었습니다.

> [!NOTE]
> ```pod``` 명령어인 ```cocoapods```이 필요하여 설치하게 되었다.

## 설치

설치 방법은 아래와 같습니다.

### rbenv 설치

먼저 버전 관리 메니저를 설치합니다

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
```

필자의 경우 zshell을 사용하기 때문에\
쉘에 대한패치를 ```~/.zshrc```에 해주었다.

```bash
echo 'eval "$(~/.rbenv/bin/rbenv init - zsh)"' >> ~/.zshrc
```

동작 확인을 해보자

```bash
rbenv -v
```

### ruby-build 설치

설치가 완료 되었다면 이제  ```rbenv install``` 을 사용할 수 있게 ```ruby-build```를 깔아줄것이다

먼저 ```ruby-build```을 플러그인을 해준다

```bash
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
```

이제 빌더를 다운받아 압축을 푼후 install.sh를 실행 시켜준다(혹은 make를 해준다)

[다운 링크](https://github.com/rbenv/ruby-build/releases/tag/v20240319)

```bash
tar -xzf ruby-build-*.tar.gz
PREFIX=/usr/local ./ruby-build-*/install.sh

## or
# make PREFIX="/usr/local"
```

> [!TIP]
> 필자의 경우 ```PREFIX```의 위치를 ```~/tools```로 지정하여 현제 사용자에 설치되게 하였다.

이것으로 설치를 완료 하였다.

```bash
ruby-build --version
```

확인이 완료되었으면 install 명령어가 정상적으로 작동하는지 확인한다.

```bash
rbenv install --version
```

### Ruby 설치

```bash
rbenv install -l
```

명령어로 버전 목록을 볼 수 있으며 필자는 ```3.1.4```버전을 설치하였다.

```bash
rbenv install 3.1.4
```

설치가 잘 되었다면

```bash
rbenv versions
```

로 목록을 확인할 수 있고

```bash
rbenv local 3.1.4
rbenv global 3.1.4
```
> [!WARNING]
> 버전이 바뀌지 않았다면 ```rbenv init```를 입력하여 나오는 eval path를 진행해준다

버전을 설정한 다음 터미널을 재시작 함으로 버전이 바뀐것을 알 수 있다.

```bash
ruby -v
```

이것으로 ruby 설치 과정은 마치도록 하겠다

## 참조

🔗 링크 rbenv : [https://github.com/rbenv/rbenv](https://github.com/rbenv/rbenv)

🔗 링크 ruby-build : [https://github.com/rbenv/ruby-build](https://github.com/rbenv/ruby-build)

## cocoapods 설치

이제 ```ruby```가 업데이트 되었으니 ```gem```을 업데이트 하고 설치를 진행해 보자

```bash
gem update
```

```cocoapods``` 설치 하기

```bash
gem install cocoapods
```

잘 설치가 되었다

```bash
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.
```

이제 이 ```Error``` 와는 안녕이다~ 👋
