# [yuujinkim.github.io](https://yuujinkim.github.io/)

<br/>

## Build 과정
### 1. Repository 생성
Github에서 \<username>.github.io 이름의 Repository 생성

### 2. Local-Remote Repository 연동
Remote Repository의 주소를 복사한 후  
`git clone <복사한 Remote Repository의 주소> <path>`로 clone

### 3. Jekyll 설치
[Windows용 Jekyll 가이드 참조](https://jekyllrb-ko.github.io/docs/installation/windows/)

[Windows용 Ruby + Devkit](https://rubyinstaller.org/downloads/)  
위의 링크를 통해 Ruby 설치

Jekyll과 Bundler를 설치  
`gem install jekyll bundler`

Jekyll이 올바르게 설치되었는지 확인  
`jekyll -v`

### 4. Jekyll 사이트 생성
현재 디렉토리(.)에 Jekyll을 설치
`jekyll new . --force`

Jekyll 시작하기  
`bundle exec jekyll serve` 을 실행 후,  
localhost:4000 접속

* LoadError 발생 시 webrick 파일 설치
`bundle add webtick`

### 5. 테마 적용하기
[다음](http://jekyllthemes.org/)에서 원하는 테마 선택

[원하는 테마](https://github.com/poole/lanyon)를 git clone해서 로컬에 받아오기

테마 파일들을 로컬 저장소에 반영하기  
이때, 의존성을 감안하여 _posts를 제외하고 테마를 덮어쓰기

### 6. Customize
블로그 포스팅은 ___posts__ 폴더에서 진행  
_post에 __YYYY-MM-DD-TITLE.md__ 형태로 새로운 문서를 작성
```
---
layout: post
title: "제목"
---
```
위와 같은 형식으로 Post 문서를 작성  
Markdown 형식을 통해 내용 작성

_config.yml의 title과 tagline, url 수정  
description 등 불필요한 부분 삭제

_includes/sidebar.html에서 사이드바 수정

### 7. 댓글 기능 추가
[Disqus](https://disqus.com) 가입  
"I want to install Disqus on my site" 선택  
사이트 정보 입력 (Website Name 기억해두기) - Category는 Tech 선택  
Platform 중 Jekyll 선택  
Configure를 눌러 Website Name에 아까 기억해 두었던 이름(yuujinkim)과 Website URL에 사이트 주소(https://yuujinkim.github.io) 입력  
Comment 정책 선택 (Balanced와 Strict 중 나는 Balanced 선택함)  
Complete Setup을 눌러 설정 마무리

_config.yml에 다음과 같은 key-value 추가
```
# Custom vars
version: 1.1.0
google_analytics_id: #UA-XXXX-Y
comment:
  provider: "disqus"
  disqus:
    shortname: "yuujinkim"
```

_layout/post.html을 페이지에 맞게 수정
```
{% if page.comments %}
<h2>Comments</h2>
<div id="disqus_thread"></div>
<script>
    /**
    *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
    *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables    */
    let PAGE_URL = "{{site.url}}{{page.url}}"
    let PAGE_IDENTIFIER = "{{page.url}}"
    var disqus_config = function () {
    this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
    this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    (function() { // DON'T EDIT BELOW THIS LINE
    var d = document, s = d.createElement('script');
    s.src = 'https://yuujinkim.disqus.com/embed.js';
    s.setAttribute('data-timestamp', +new Date());
    (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
{% endif %}
```

댓글을 허용하고 싶은 곳에 `comments: true`로 지정

### 8. Personal Access Token(PAT) 생성하기
github-Setting-Developer settings-Personal access tokens-Generate new token  
Note(토큰 메모), Expiration(유효기간), Scope(권한 범위) 결정 후 생성  

토큰은 다시 볼 수 없으니 잘 기억해두기

### 9. Github Page 시작하기
파일 스테이징 `git add <파일명>`

파일 커밋 `git commit -m "<커밋 메시지>"`

현재 branch의 이름을 main으로 변경 `git branch -M main`

원격 저장소에 반영 `git push origin main`

Password에 PAT을 입력

### 10. 원격에서 깨지는 문제 해결
localhost:4000에서는 잘 나오는데 [원격](https://yuujinkim.github.io/)에서는 내용이 깨져서 나오는 문제 발생

_config.yml에서 baseurl 삭제  
url은 https://yuujinkim.github.io/ 로 수정

### 11. jekyll-admin
Gemfile에 추가
`gem 'jekyll-admin', group: :jekyll_plugins`

plugin 설치
`bundle install`

jekyll 실행 `bundle exec jekyll serve`

localhost:4000/admin 접속

![jekyll-admin](https://user-images.githubusercontent.com/66306573/146342490-e3eff6bc-7379-4273-aa1e-140403eb28c6.PNG)

### 12. 사이트에 favicon 추가
**파비콘(favicon)이란?**　　![](https://user-images.githubusercontent.com/66306573/146344595-f8a0b2a2-46e1-4adc-861a-aa1c94644b2e.PNG)
> 즐겨찾기 아이콘. 즐겨찾기(favorites)와 아이콘(icon)의 합성어로, 주소창에 조그만 아이콘으로 표시

[favicon 변환 사이트](https://www.favicon-generator.org/)에서 원하는 이미지를 아이콘(.ico) 형식으로 변경

이름을 favicon.ico로 만든 후  
public/favicon.ico에 저장하여 favicon 적용
