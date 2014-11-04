---
layout: post
title:  문자열 함수
date:   2014-10-14 22:02:13
categories: jekyll update
---
#문자열 함수
## 1. 문자열 함수

오늘은 문자열 함수와 메모리 구조에 대해서 알아보도록 하겠습니다. 먼저 문자열 함수에 대해 알아보도록 할텐데, 문자열 함수에는 많이 알려져있는 함수들인 strcpy, strncpy, strcat, strncat, strcmp 등 이밖에도 함수가 더 있지만 매우 유용하고 헤더 선언부에 string.h를 포함하겠다고 선언하면 이 함수들을 모두 사용하실 수 있게됩니다.

첫번째로 만나볼 함수 strcpy(문자열 복사, String Copy)는 말 그대로 문자열 복사에 관한 함수입니다. strcpy 함수의 원형을 살펴보자면 아래와 같습니다.

`char* strcpy (char *dest, const char *src); // dest에 전달된 값을 반환`

이 함수는 두개의 문자형 포인터를 인수로 취하며 src이 가르키는 문자열을 dest가 가르키는 곳에 NULL 문자까지 포함하여 복사합니다. 앞에서 만날 strncpy와 달리 strcpy 함수는 src 문자열 에서 널(NULL) 문자를 만날때까지 dest로 복사됩니다. 

```
#include <stdio.h>
#include <string.h>
 
int main()
{
    char str1[]="exynoa";
    char str2[7];
     
    strcpy(str2, str1);
    printf("%s\n", str2);
    return 0;
}


```

```
<결과>
exynoa

```

9행에서 strcpy 함수가 쓰였는데 str1 문자열이 str2에 복사가 됬는지 확인하기 위해 str2를 출력하도록 했습니다.
주의하실 점은 dest가 가르키는 배열의 크기가 src 보다 크거나 같아야 합니다. (오버플로우 발생 우려)

`char* strncpy (char *dest, const char *src, size_t n);
`
strncpy 함수는 strcpy와 기능이 같지만 NULL까지의 복사가 안되며 n바이트 까지 복사가 됩니다. 만약 src가 가르키는 문자열의 길이가 n보다 작다면 나머지 공간은 널문자로 채워집니다.

```
/*  public.boulder.ibm.com에서 가져온 예제 */
#include <stdio.h>
#include <string.h>
  
#define SIZE    40
  
int main(void)
{
  char source[SIZE] = "123456789";
  char destination[SIZE] = "abcdefg";
  
  /* strcpy의 작동 방식 */
  printf("원래 destination가 가르키는 값 = '%s'\n", destination);
  strncpy(destination, source, 5);
  printf("strncpy 후, destination의 값 '%s'\n", destination);
}


```

```
<결과>
원래 destination가 가르키는 값 = 'abcdefg'
strncpy 후, destination의 값 '12345fg'
계속하려면 아무 키나 누르십시오 . . .

```

13행에서 strncpy 함수로 인해 source가 destination로 5의 길이만큼 복사됩니다. 따라서 12345가 destination로 복사되며(abcde가 있던 공간에 12345로 복사) 12345fg를 출력하게 됩니다.

strlen 함수는 문자열의 길이를 계산해서 반환하는 함수입니다.

`size_t strlen(const char *string); // NULL 문자를 포함하지 않고 길이반환<br>
`

아래에 예제가 있습니다.

```
#include <stdio.h>
#include <string.h>
 
int main()
{
    char str1[]="프로그래밍";
    char str2[]="Programming";
    char str3[]="123456789";
    printf("str1의 길이는 %i 입니다.\n", strlen(str1));
    printf("str2의 길이는 %i 입니다.\n", strlen(str2));
    printf("str3의 길이는 %i 입니다.\n", strlen(str3));
}

```

```
<결과>
str1의 길이는 10 입니다.
str2의 길이는 11 입니다.
str3의 길이는 9 입니다.
계속하려면 아무 키나 누르십시오 . . .

```

결과를 보고 코드를 볼때, 한글은 한글자 당 2바이트로 표시되며 NULL 문자가 포함되지 않습니다.

strcat, strncat 함수는 두개의 문자열을 연결하는 기능을 제공하는 함수입니다.

```
char *strcat(char *dest, const char *src);
char *strncat(char *dest, const char *src, size_t n);<br>


```

이 두 함수는 src가 가르키는 문자열을 dest가 가르키는 곳의 끝인 '\0' 위치부터 붙여 넣습니다. (NULL 문자 포함) strcat와 strncat의 차이점은 strcpy와 strncpy 함수와의 차이점과 동일하며, 즉 strncat의 세번째 전달인자는 문자열의 뒤에 복사할 문자열의 최대길이를 제한합니다.


```
#include <stdio.h>
#include <string.h>
 
int main()
{
    char src[20]="GRAMMING";
    char dest[20]="PRO";
     
    strcat(dest, src);
    printf("dest의 문자열은 %s\n", dest);
} 


```

```
<결과>
dest의 문자열은 PROGRAMMING
계속하려면 아무 키나 누르십시오 . . . 

```

9행에서 strcat를 이용하여 src를 덧붙일때 dest에 있던 널문자는 삭제가 됩니다. 

strcmp와 strncmp 함수는 두 문자열이 서로 동일한지 확인하고 싶을때 쓰이는 함수입니다.

```
<p>int strcmp(const char *s1, const char *s2);
int strncmp(const char *s1, const char *s2, size_t n);<br></p>


```

두 문자열이 동일하면 0을 반환하는데 동일하지 않다면 사전편찬 순서상 s1이 s2보다 사전의 앞부분에 위치하면 음수를, s2가 s1보다 사전의 앞부분에 위치하면 양수를 반환합니다. 이는 차례차례 비교를 하다 처음으로 다른문자가 발견되면 그 두문자의 아스키코드 값을 뺀후 그 값을 반환하기 때문입니다. strncmp는 지정한 곳까지만 문자열을 비교하는 함수입니다.


```
/*  public.boulder.ibm.com에서 가져온 예제 */
#include <stdio.h>
#include <stdlib.h>
#define SIZE 10
  
int main(void)
{
  int  result;
  int  index = 3;
  char buffer1[SIZE] = "abcdefg";
  char buffer2[SIZE] = "abcfg";
  void print_result(int, char *, char *);
  
  result = strcmp( buffer1, buffer2);
  printf("각 문자의 비교\n");
  printf("strcmp: ");
  print_result(result, buffer1, buffer2);
  
  result = strncmp(buffer1, buffer2, index);
  printf("\n%i 길이 까지의 문자 비교\n", index);
  printf("strncmp: " );
  print_result(result, buffer1, buffer2);
}
  
void print_result( int res, char * p_buffer1, char * p_buffer2)
{
  if ( res == 0 )
    printf("\"%s\" 와 \"%s\"는 동일합니다.\n", p_buffer1, p_buffer2);
  else if ( res < 0 )
    printf("앞서는 문자열: \"%s\"\n", p_buffer1);
  else
    printf("앞서는 문자열: \"%s\"\n", p_buffer2);
}


```

```
<결과>

각 문자의 비교
strcmp: 앞서는 문자열: "abcdefg"
3 길이 까지의 문자 비교
strncmp: "abcdefg" 와 "abcfg"는 동일합니다.
계속하려면 아무 키나 누르십시오 . . .


```

buffer1과 buffer2에 각각 문자열을 저장하고 print_result란 함수로 문자열의 대소를 비교하여 어느쪽이 크거나 작은지 출력합니다. 14행에서 strcmp 함수를 사용해 두 문자열을 비교하고 반환되는 값을 result에 저장하고 print_result에 result, buffer1, buffer2를 전달하여 결과를 출력합니다. 결과를 보면 사전편찬 순서상 buffer1이 출력되었습니다. 다시 코드로 돌아와 19행에서 strncmp 함수를 사용하여 두 문자열을 비교하고 반환되는 값을 result에 저장합니다. 여기서 주의하셔야 할것은 strcmp완 달리 지정된 길이까지만 비교하므로 buffer1을 예로 들어 "abcdefg"가 아닌 "abc"까지만 비교를 합니다. 결과를 보면 두 문자열에서 abc 까지 동일하므로 0이 반환되어 동일하다는 결과를 얻을수 있습니다.

strtok 함수는 문자열을 토큰으로 자르는 기능을 합니다. 여기서 토큰(token)이란 1996/11/02란 문자열을 구분자 /로 자르면 1996, 11, 02란 문자열로 분할을 할수 있습니다. 한마디로 토큰은 특정 조건에 의해서 구분이 되는 문자열의 일부를 말합니다.


```
char *strtok(char *str, const char *set);
// 다음 번 토큰 주소의 값을 반환, 반환할 토큰이 존재하지 않으면 NULL 반환<br>


```

아래 예제를 보시면 좀더 확실히 이해하실수 있습니다.


```
/* 예제: www.cplusplus.com/reference/clibrary/cstring/strtok/  */
#include <stdio.h>
#include <string.h>
 
int main ()
{
  char str[] ="- This, a sample string.";
  char * pch;
  printf ("문자열 \"%s\"을 토큰으로 분리:\n",str);
  pch = strtok (str," ,.-");
  while (pch != NULL)
  {
    printf ("%s\n",pch);
    pch = strtok (NULL, " ,.-");
  }
  return 0;
} 


```

```
<결과>
문자열 "- This, a sample string."을 토큰으로 분리:
This
a
sample
string
계속하려면 아무 키나 누르십시오 . . .

```



10행에서 strtok 함수가 첫번째로 호출되어 ,.- 구분자들로 인해 토큰이 나뉘고 첫번째 토큰의 주소값이 반환됩니다. 14행의 두번째 호출부터는 첫번째 인수자리에 NULL를 기입함으로써 토큰을 계속 찾을수 있습니다. 이렇게 구분자로 문자열을 나누고 더이상 토큰이 존재하지 않아 NULL이 반환되므로 루프를 빠져나옵니다.

