---
# layout: post
title: "[Git] 로컬에서 지킬 블로그 실행해보기 !"
date: 2019-09-23 15:20:14
categories: github jekyll
comments: true
---
  
  
지킬로 블로그를 만든 지 약 2~3주 정도 흘렀다. 지킬은 생초보고 git도 써봤지만 다 까먹었기 때문에 꿋꿋이 깃헙 사이트에서 모든 것을 CRUD 했다.... 
그 결과 7개의 포스트만(심지어 반은 쓰다 말았다) 올렸음에도 불구하고 201번의 커밋을 하였다 ^^  
  
![git commit](https://user-images.githubusercontent.com/41671001/65405016-e76ef980-de15-11e9-87f3-3698c7c07680.png)  
<font style="color:#808080">언제 이렇게 많이 했을까...</font>  
  
뭐 잘 모르겠지만 구글링해보니 눈치상 마크다운 편집기도 있는 것 같고.. 다들 나처럼 이렇게 한 글자 고치고 커밋을하는 
뻘짓을 안하고 로컬에서 확인하시는 것 같은데 난 일단 .. 깃도 쓸 줄 모른다..까먹었다... 지금 해봤자 미래의 나는 또 까먹을 것이 뻔하기 때문에 포스팅해둔다.  
숨 쉬듯 커밋은 이 글을 마지막으로 끝내고 싶다...

## 설치하기(윈도우 기준)  
1. [Git for Windows](https://gitforwindows.org){:target="_blank"}  
2. [Ruby for Windows](https://rubyinstaller.org/){:target="_blank"}  
일단 두 개를 설치한다!...  
구글링하는데 자꾸 루비 루비 노래를 부르길래 무엇인가 했더니 지킬이 루비로 만들어졌다고 한다...^^...난 뭘까?...  
그냥.. 들어가서 맨 위의 것 받아서 다음>다음>다음> 설치 완료된다.    
  
* 참고 : 순서는 내 맘대로임  
  
### 1. Ruby에 Jekyll 설치  
![ruby](https://user-images.githubusercontent.com/41671001/65407463-8e0ac880-de1d-11e9-8a1c-db65a2cfec39.png)  
Start Command Prompt with Ruby 프로그램을 실행하면 1,2,3 중에 하나를 입력하라고하는데 <strong>3을 입력</strong>한다.  
스크린샷엔 1이라고 되어있는데... 개발도구를 같이 설치해야 편하다고해서 3으로 했다.  
  
![install jekyll](https://user-images.githubusercontent.com/41671001/65408952-89e0aa00-de21-11e9-91cd-ee0e068886b6.png)  
```
gem install jekyll bundler
```
그리고 지킬을 설치해주고  
  
```
jekyll -v
> jekyll 4.0.0
```
설치가 되었는지 버전을 확인해본다.  

### 2. 블로그 가져오기  
```
git clone [URL]
```  
그리고 work 폴더에 프로젝트를 가져온다.(바로 되니 캡쳐 생략)  
  
### 3. 로컬에 지킬 띄우기  
```
jekyll serve
```
지킬 로컬에 띄우는 명령어같은데...  
여기서 정상적으로 넘어갔다면  
http://127.0.0.1:4000/ 으로 접속하면 뜬다고한다...  
  
  
  
<details>
  <summary>+ 삽질................</summary>
<div markdown="1">
하지만 나는 오류가 난다^^ 바로 될리가 없지...  
  
```  
C:\work>jekyll serve
Configuration file: none
            Source: C:/work
       Destination: C:/work/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
          Skipping: sbeeeeeeen.github.io/_posts/2019-09-23-git-bash-1.md has a future date
  Liquid Exception: Could not locate the included file 'gallery' in any of ["C:/work/_includes"]. Ensure it exists in one of those directories and, if it is a symlink, does not point outside your site source. in sbeeeeeeen.github.io/about.md
```  
Liquid Exception은 뭐란 말인가............  
구글링했으나 뭐라는지 모르겠다...  
  
gallery?.... 이런 파일도 있었나... 모르겠으니 쿨하게 삭제하고 다시 시도했는데..안된다...약간 때려치고 싶다...  
그냥 about.md 파일에서 gallery 쓰는 줄을 없애버렸다.. 어차피 테마 그대로 가져온 거라....  
혹시 몰라서 gallery파일에서 include는 includes로 바꿨다([스택오버플로우에서 누가 해보라고했다](https://stackoverflow.com/questions/47624711/could-not-locate-the-included-file-error){:target="_blank"})  
  
암튼.. 둘 다 하고 다시 jekyll serve 해보니  
  
```
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'sbeeeeeeen.github.io/assets/css/main.scss':
                    Error: File to import not found or unreadable: minimal-mistakes/skins/default. on line 3:1 of main.scss >> @import "minimal-mistakes/skins/default"; // skin ^
```  
ㅜ.. 저기요...   
[하지만 나와 같은 사람은 또 있었다...](https://github.com/mmistakes/minimal-mistakes/issues/1244){:target="_blank"}  
  
해주고 나면  
```
Configuration file: none
            Source: c:/work
       Destination: c:/work/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
          Skipping: sbeeeeeeen.github.io/_posts/2019-09-23-git-bash-1.md has a future date
     Build Warning: Layout 'categories' requested in sbeeeeeeen.github.io/category-archive.md does not exist.
     Build Warning: Layout 'home' requested in sbeeeeeeen.github.io/index.html does not exist.
  Conversion error: Jekyll::Converters::Scss encountered an error while converting 'sbeeeeeeen.github.io/assets/css/main.scss':
                    Error: Invalid CSS after '...harset "utf-8";': expected 1 selector or at-rule, was '# @import "minimal-' on line 1:18 of main.scss >> @charset "utf-8"; -----------------^
```  
뭐 끝이 없네... 그냥 import에 # 하나 박으면 주석처리 될 줄 알았는데 안먹은 것 같다... 그냥 그 라인 없애고 다시 시도...  
  
```
 Conversion error: Jekyll::Converters::Scss encountered an error while converting 'sbeeeeeeen.github.io/assets/css/main.scss':
                    Error: File to import not found or unreadable: minimal-mistakes. on line 3:1 of main.scss >> @import "minimal-mistakes"; // main partials ^
```
내가 뭘 잘못했을까............ 

</div>
</details>
  



## Reference  
- [깃 허브 페이지 로컬에서 실행하기](https://m.blog.naver.com/PostView.nhn?blogId=spring1a&logNo=221335758311&proxyReferer=https%3A%2F%2Fwww.google.com%2F){:target="_blank"}  
- [Jekyll 설치 및 로컬에 띄우기](https://17billion.github.io/jekyll/install/2017/05/27/install-a-jekyll.html){:target="_blank"}  
- [Windows에서 Github와 Jekyll 개발 환경 설치하기](https://wormwlrm.github.io/2018/07/13/How-to-set-Github-and-Jekyll-environment-on-Windows.html){:target="_blank"}  
