---
title: Go language 구경
layout: post
---

[A Tour of Go][tour]을 발견했는데,흥미로워서 따라가보았다. 

[golang][golang]은 왜 만들었을까? 특히 이미 많은 언어들이 존재하는데. 이에 대해 Rob Pike은 다음과 같은 문제들 때문에 새로운 언어을 만들었다고 한다.

- Computers fast but software construction slow. 
- Dependency analysis necessary for speed, safety. 
- Types get in the way too much.
- Garbage collection, concurrency poorly supported. 
- Multi-core seen as crisis not opportunity.

C나 C++과 다르게 컴파일시에 의존성 검사에서 빠르고,GC을 도입하여 개발자들이 직접 메모리관리를 하지 않게 해서 좀더 쉬운 프로그래밍 모델을 지원하고, Java가 Thread을 기본으로 고려해서 만든것 처럼, 새로 만든 언어 답게 Multi-core나 Concurrency을 위해 고려된 점[^1] ,정적 타입의 언어이지만, 가벼운 타입 시스템을 지원하는 특징이 있는 듯 하다. 

# Hello,世界

{% highlight python %}
package "main"

import "fmt"

func main() {
    fmt.Print("Hello, 世界\n")
}

{% endhighlight %}

패캐지 외부에서 접근 하는 공개된 함수나 값은 대문자로 시작되어야 한다. 
자바에서처럼 public,protected,private와 같은 접근제한자가 따로 없이, 대/소문자로만 결정되어 진다. 



[golang]: http://golang.org/
[tour]:  http://tour.golang.org/
[gopher]: http://www.google.com/search?q=gopher&hl=ko&client=safari&rls=en&prmd=imvns&tbm=isch&tbo=u&source=univ&sa=X&ei=yYDHTs2gFLGImQWIzIn8Dw&ved=0CGAQsAQ&biw=1440&bih=713#hl=ko&client=safari&rls=en&tbm=isch&sa=1&q=gopher+golang&pbx=1&oq=gopher+golang&aq=f&aqi=&aql=&gs_sm=e&gs_upl=3950l4868l0l5022l7l5l0l1l0l0l246l708l0.2.2l4l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a29d1d988535754f&biw=1440&bih=713
[^1]: goroutine/channel  

