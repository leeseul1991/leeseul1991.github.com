---
layout: post
title:  함수
date:   2014-10-25 19:55:16
categories: jekyll update
---

#함수의 정의와 사용
## 1. 함수의 정의

이번편에서는 함수(Function)에 대해서 알아보도록 하겠습니다. 함수란 뭘까요? 이 함수란 것은, 특정한 작업을 수행하는 또는 서로 관련있는 코드들의 모임으로 하나의 단위를 말합니다. 이 함수란 것은 모듈(module) 이라고도 하며, 우리가 배우는 C언어는 모듈러 프로그래밍(modular programming)이기도 합니다. 즉, 모듈(=함수)가 중심이 되는 언어로써, 재사용이 가능하고 유지 보수가 쉬워진다는 등 여러가지 장점을 지니고 있습니다.

<img src="http://cfile24.uf.tistory.com/image/1972564651405F550624DB" width="500" height="500">

**<프로그램에선 여러개의 함수가 각각 하나의 부품처럼 동작한다>**
_ _ _

우리가 알고있는 프로그램은 함수로 구성되어 있고 그 함수들이 순차적으로 실행됨으로 프로그램이 정상적으로 작동합니다. 이는 독립적인 기능을 지니며 프로그램을 구성하는 부품이라 할수 있습니다. 프로그램이 해야 할일은 모두 함수가 담당하며 핵심인 메인 함수아래서 체계적으로 실행됩니다. 함수는 다양한 곳에서 접할수 있습니다. 중고등부 수학에서라던지, 반복해서 무언갈 만들고 있는 기계에서까지! 본격적으로 이해하고 그 다음 우리가 함수를 사용하고 프로그램을 만들어 보도록 합시다.

```
<데이터 타입> 함수명(매개변수1, 매개변수2, ...)
{
  함수 본체;
}
```

여기서 데이터 타입은 만약에 정수형 데이터를 반환(return)하게 된다면 int를, 실수형을 반환하게 된다면 double를, 반환하는 값이 없다면 void를 쓰게 됩니다. 데이터 타입란에 void가 아닌 다른 자료형 혹은 사용자가 정의한 자료형 등이 왔다면 그 자료형에 맞게 반환을 해주어야 한다는 것을 기억하고 계세요. 이어서 함수명은 우리가 이 이름으로 함수를 호출*하게 되는데 함수의 기능을 제대로 표현해 줄 수 있는 이름이 좋습니다. 매개변수 목록은 함수를 호출할 때 우리가 어떠한 값을 함수에게 넘겨주려면 이곳에 매개변수의 데이터 타입과, 매개변수의 이름을 제대로 명시해야 합니다. (함수의 세부적인 사항은 추후 강좌를 진행하면서 설명합니다.)

* 호출(call): 우리가 알고있는 호출. 즉, '함수를 부른다'라고 생각하시면 됩니다.


## 2. 함수의 사용
간단하게 함수의 정의를 알아보았고, 이제는 함수를 우리가 직접 정의하여 호출을 해보도록 하겠습니다. 우선 반환형이 int형이고, 두 수를 덧셈하여 결과를 돌려주는 함수를 만들어볼 것이므로 두개가 필요하겠죠? 아래 예를 한번 보고, 함수가 어떤 것인지 간단하게 살펴보도록 합시다.

```
#include <stdio.h>
 
int sum(int a, int b) {
    return a + b;
}
 
int main()
{
    int a, b;
 
    scanf("%d%d", &a, &b);
    printf("a의 값: %d\n", sum(a, b));
    return 0;
}

```

```
<결과>
20 30
a의 값: 50
계속하려면 아무 키나 누르십시오 . . .

```

3행에서 sum이란 함수를 정의했으며 a와 b값을 인수로 전달할수 있도록 하였고, sum 함수 호출시 전달받은 a와 b를 더하여 반환(return)하도록 하였습니다. 그리고 메인함수에서 사용자로부터 a와 b값을 입력받아 sum을 호출하고 a + b의 결과값을 출력 하였습니다. 간단하게 정리하여 보면, 우리가 만약 10과 20이란 값을 a와 b에 넣어 sum의 매개변수로 넘겨주면 그 a의 값과 b의 값을 더한 값이 돌아오는 즉, 반환하여 그 값을 출력합니다. sum(a, b) 자리에 10과 20을 더한 30이란 값이 돌아온다는 소리입니다.

또 다르게, 우리가 5와 4란 값을 입력하면 sum 함수를 호출하여 9를 반환하고 그 값을 출력하는걸 볼 수 있습니다. 데이터를 전달하기 위해 선언되는 변수(3행의 a와 b)를 매개변수(parameter)라고 합니다. 그리고 이렇게 정의된 함수는 우리가 호출하고 싶을때 몇번이든지 호출이 가능하며 함수를 사용하기 전 메인 함수가 등장하기 전에 정의되야 하거나 컴파일러에게 함수가 정의되어 있음을 알리기 위해 프로토타입(prototype)으로 선언해야 합니다. 만약에 sum 함수를 프로토 타입으로 선언하게 되면 뒤에서 sum 함수가 나올것이라는 것과 어느 인수를 요구하는지 알릴수 있게 됩니다. 이 예제의 sum 함수를 프로토 타입으로 선언하면 다음과 같습니다.

```
#include <stdio.h>
 
int sum(int a, int b);
 
int main()
{
    int a, b;
 
    scanf("%d%d", &a, &b);
    printf("a의 값: %d\n", sum(a, b));
    return 0;
}
 
int sum(int a, int b) {
    return a + b;
}

```


위 예제는 처음 예제와는 다른점이 없으며 그저 sum 함수를 프로토 타입으로 선언하였다는 것밖에 존재하지 않습니다. (여기서 프로토타입 선언은, 메인 함수가 정의된 코드 뒤에 정의된 함수를 호출하게 된다면 호출된 함수의 이름을 찾을 수 없어 오류가 발생하게 됩니다. 그렇기 때문에, 메인 함수가 정의되기 이전에 이러한 함수가 있음을 알려주어야만 호출이 가능합니다.) 여기서 매개변수는 전달되는 데이터 값을 임시로 저장하기 위한 저장공간일 뿐이지 굳이 a, b로 하시지 않고 어떻게 작성하던 결과값에는 영향을 미치지 않습니다. 

예를 들어서, Swap이란 함수를 정의하고, 매개변수 a와 b의 값을 서로 바꾸는 기능을 하는 함수라도 실제로 넘어간 a의 b의 값이 서로 바뀌지는 않는다는 겁니다. 매개변수 a와 b, 그리고 호출할때 넘겨준 a와 b는 다른 변수입니다.



<!DOCTYPE html>

<!--[if IE 8]><html lang="ko" dir="ltr" class="ie8"><![endif]-->
<!--[if IE 9]><html lang="ko" dir="ltr" class="ie9"><![endif]-->
<!--[if gt IE 9]><!--><html lang="ko" dir="ltr"><!--<![endif]-->
<head>
    <title>디스커스 댓글</title>

    
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
    <meta http-equiv="X-UA-Compatible" content="IE=edge"/>

    
    <style>
        html {
            overflow: hidden;
        }
        
    </style>

</head>
<body>
    
    <!--[if lte IE 8]>
<script src="//a.disquscdn.com/1414604865/build/vendor/ie8.js"></script>
<![endif]-->
<!--[if IE 9]>
<script src="//a.disquscdn.com/1414604865/build/vendor/ie9.js"></script>
<![endif]-->

    
<script type="text/json" id="disqus-urls">{
    "root":"//disqus.com",
    "next":"//a.disquscdn.com/next/1db76087"
}</script>

    

    <div id="error" style="display:none; text-align: center">
        <p>Disqus를 로드하지 못했습니다. 혹시 관리자시라면 저희 <a href="http://docs.disqus.com/help/83/">문제 해결 가이드</a>를 보세요.</p>
    </div>

    
    <script type="text/json" id="disqus-forumData">{"session":{"isReadOnly":null,"canModerate":false,"audienceSyncVerified":false,"canReply":true,"mustVerifyEmail":false},"features":{},"forum":{"name":"AlphaFactory","language":"ko","settings":{"canEnableSponsoredComments":false,"discoveryVariant":"default","allowAnonPost":false,"allowMedia":true,"moderatorText":"Admin","typeface":"auto","disable3rdPartyTrackers":false,"promotedDiscoveryEnabled":false,"discoveryMax":false,"ssoRequired":false,"discoveryLocked":false,"audienceSyncEnabled":false,"hasCustomAvatar":true,"organicDiscoveryEnabled":true,"discoverySettingsUrl":"https://alphafactory.disqus.com/admin/settings/ads/","discoveryThumbnailsEnabled":false,"colorScheme":"auto","sponsoredCommentsEnabled":false,"linkAffiliationEnabled":true},"url":"http://www.alphafactory.co.kr/","guidelines":null,"favicon":{"permalink":"http://disqus.com/api/forums/favicons/alphafactory.jpg","cache":"//a.disquscdn.com/1414604865/images/favicon-default.png"},"avatar":{"small":{"permalink":"http://disqus.com/api/forums/avatars/alphafactory.jpg?size=32","cache":"//a.disquscdn.com/uploads/forums/270/2177/avatar32.jpg?1386132599"},"large":{"permalink":"http://disqus.com/api/forums/avatars/alphafactory.jpg?size=92","cache":"//a.disquscdn.com/uploads/forums/270/2177/avatar92.jpg?1386132599"}},"pk":2702177,"founder":"22206849","raw_guidelines":null,"id":"alphafactory","channel":null}}</script>

    
    <script type="text/json" id="disqus-threadData">{"cursor":{"hasPrev":false,"prev":null,"total":0,"hasNext":false,"next":"1:0:0"},"code":0,"response":{"lastModified":1395655558,"posts":[],"thread":{"feed":"https://alphafactory.disqus.com/jekyll_20140129_49/latest.rss","uploadAdd":"//alphafactory.disqus.com/thread/jekyll_20140129_49/async_media_upload/","identifiers":[],"dislikes":0,"likes":0,"message":"","id":"2189432805","isDeleted":false,"category":"2743455","clean_title":"Jekyll \ud14c\ub9c8 \ub9cc\ub4e4\uae30 2014/01/29","userScore":0,"userSubscription":false,"createdAt":"2014-01-29T08:10:51","hasStreaming":false,"uploadRemove":"//alphafactory.disqus.com/thread/jekyll_20140129_49/async_media_remove/","raw_message":"","isClosed":false,"link":"http://www.alphafactory.co.kr/post/2014/01/29/making-custom-jekyll-theme/","slug":"jekyll_20140129_49","forum":"alphafactory","author":"22206849","posts":0,"moderators":[22206849],"title":"Jekyll \ud14c\ub9c8 \ub9cc\ub4e4\uae30 2014/01/29","highlightedPost":null}},"order":"asc"}</script>

    

    <div id="fixed-content"></div>

    <script src="//a.disquscdn.com/next/1db76087/lounge.load.js" id="bootstrap-script" data-app="lounge"></script>
</body>
</html>

