---
title: "[TravisCI] Your bundle only supports platforms "x64-mingw32" but ~ 오류 수정"
date: 2019-10-07 15:04:58
categories: git TravisCI
comments: true
---
  
<br>  
  
```
Your bundle only supports platforms ["x64-mingw32"] but your local platforms are
["ruby", "x86_64-linux"], and there's no compatible match between those two
lists.
```  
언젠가부터 Travis CI에서 계속 똑같은 오류가 났다. 굳이 수정안해도 돌아가긴해서 냅뒀다가.. 영 거슬려서 
또 구글링을 시작했다.....  
  
[[SOLVED] How can I resolve "Your bundle only supports platforms ["x86-mingw32"] but your local platforms are ["ruby", "x86_64-linux"]"](https://tutel.me/c/programming/questions/43429685/how+can+i+resolve+quotyour+bundle+only+supports+platforms+quotx86mingw32quot+but+your+local+platforms+are+quotrubyquot+quotx86_64linuxquotquot){:target="_blank"}  
나랑 똑같은 사람은 역시나 항상 있다...  
  
글에 나온 그대로 실행해주고  
  
```
C:\Users\test\sbeeeeeeen.github.io>bundle lock --add-platform ruby
Fetching gem metadata from https://rubygems.org/..........
Fetching gem metadata from https://rubygems.org/.
Resolving dependencies...
Writing lockfile to C:/Users/sbyim/Desktop/test/sbeeeeeeen.github.io/Gemfile.lock

C:\Users\test\sbeeeeeeen.github.io>bundle lock --add-platform x86_64-linux
Fetching gem metadata from https://rubygems.org/..........
Fetching gem metadata from https://rubygems.org/.
Resolving dependencies..........................................................................................................................................................................................................................................................................................................................................................................................................................................
Writing lockfile to C:/Users/sbyim/Desktop/test/sbeeeeeeen.github.io/Gemfile.lock
```
  
push를 하였으나 오류가 난다... 놀랍지도 않다ㅎ  
  
```
$ bundle install --jobs=3 --retry=3 --deployment --path=${BUNDLE_PATH:-vendor/bundle}
You are trying to install in deployment mode after changing
your Gemfile. Run `bundle install` elsewhere and add the
updated Gemfile.lock to version control.
You have deleted from the Gemfile:
* wdm (~> 0.1.0)
The command "eval bundle install --jobs=3 --retry=3 --deployment --path=${BUNDLE_PATH:-vendor/bundle} " failed. Retrying, 2 of 3.
```  
  
`Gemfile.lock` 파일을 삭제하고, `bundle install`을 실행한 후에 다시 `Gemfile.lock`을 `push`하였더니  
기존의 오류가 다시 났다........ 여보슈.....  
  
그래서 위의 `bundle lock add` 다시 해주고, `Gemfile`에서 `wdm`을 삭제했다.  

```
You have deleted from the Gemfile:
* wdm (~> 0.1.0)
```  
.....................................................  
없앴는데 왜 없애라는 거지?  
난 의지의 한국인이니까 또 도전해본다  
  
이번엔  
```
bundle install
```  
해주고 다시 push했더니!  
  
```
Done. Your build exited with 0.
```  
오류가 사라졌다~ 이게 이렇게 기쁠 일??  
  
  

