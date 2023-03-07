```include<stdio.h>
int main(void)  
{  
 printf("To C, or not to C: that is the question.\n");  
  
 return 0;  
}
```

위 코드는 짧고 간결하지만, 실제로 실행하는 것은 생각보다 가벼운 일이 아니다.

C 언어의 경우 다음 세 가지의 과정이 필요하다  
1. 전처리  
프로그램은 우선 전처리기에 보내지는데 전처리기는 #으로 시작하는 지시어의 명령을 먼저 따른다.  
```#include```와 같은 지시어를 먼저 적용한다는 것이다. 전처리기는 마치 에디터와 같다고 볼 수 있다. 프로그램에 무언가를 추가하고 수정할 수 있기 때문이다  

2. 컴파일  
수정된 프로그램은 컴파일러로 보내지는데, 여기서 코드는 기계어 명령문으로 번역이 된다.  

3. 링킹  
마지막 단계에선 링커가 컴파일에 의해 생성된 목적 코드를 프로그램을 실행하기 위해 필요한 부가 코드와 합친다.  
이 부가 코드는 보통 라이브러리 내부의 명령문인데, 위의 코드에서는 ```printf```가 되겠다.  

다행히도 위 과정은 전부 자동으로 처리되기에 부담을 가질 필요는 없다.  
전처리 과정도 컴파일러에 보통 추가가 되어있기에 전처리가 진행되고 있다는 사실조차 인지하지 못할 수도 있다.  
컴파일과 링크를 하기 위한 명령들은 컴파일러에 따라, 운영체제에 따라 다르기에 상황에 맞게 사용해야한다.  
UNIX의 경우 : % cc pun.c - UNIX에선 C컴파일러가 보통 ```cc```라고 불리기에 앞의 코드와 같이 사용한다.  
% : 프롬프트를 의미한다  
GCC의 경우 : 가장 유명한 컴파일러 중 하나. 리눅스에서 기본 제공되는 컴파일러  
사용 방법 : % gcc -o pun pun.c - pun.c 프로그램을 pun이라는 이름으로 생성  

통합개발환경을 이용하면 위의 커맨드를 입력하지 않고도 컴파일, 링크가 가능하다.  
심지어는 디버깅까지 해주기에 IDE를 많이들 사용한다. 하지만, 입문 단계에서는 전처리 - 컴파일 - 링킹으로 이뤄지는 과정을 확인해보는게  
중요하다고 생각하기에, 실습을 하게 된다면 ```GCC```를 사용해볼 예정이다.  

```C 프로그래밍: 현대적 접근 2-5 시작``` 

```scanf```와 ```printf```에 사용된 ```f```는 형식화(formatted)의 약자이다.  
그러므로 scanf와 printf는 각각 데이터를 입력받거나 출력할 때 형식 문자열(format string)이 필요하다.

예시)
```
scanf("%d", &i); //정수를 받아 i에 저장한다.
scanf("%f", &x); //소수를 받아 x에 저장한다.
```
dweight.c
```
#include <stdio.h>

int main(void)
{
  int height;
  int length;
  int width;
  int volume;
  int weight;
  
  printf("Enter height of box: ");
  scanf("%d", &height);
  printf("Enter length of box: ");
  scanf("%d", &length);
  printf("Enter width of box: ");
  scanf("%d", &width);
  
  volume = height * lenght * width;
  weight = (volume + 165) / 166;

  printf("Volume (cubic inches): %d\n",  volume);
  printf("Dimensional weight (pounds): %d\n", weight);
  
  return 0;
}
```

위의 dweight.c는 한 가지 단점이 있는데, 사용자가 숫자가 아닌 다른 값을 입력하면 에러가 발생한다.  
이에 대한 해결방안은 3-2에서 다룬다. 

```2-6 상수 이름 정의하기```
```dweight.c``` 프로그램은 ```166```이라는 상수가 존재한다. C 언어에서 상수는 매크로 정의(macro definition)을 사용하여  
상수에 이름을 붙여줄 수 있다. + 매크로 정의 때 상수를 소괄호로 둘러 표현하는 습관을 기를 것.

예시
```#define INCHES_PER_POUND (166)```
```#define```은 ```#include```와 같은 전처리 지시자이기에 세미콜론이 문장 끝에 붙지 않는다.  
프로그램이 컴파일 될 때 전처리자는 매크로를 지정된 값으로 대체한다.

예시
```
weight = (volume + INCHES_PER_POUND -1) / INCHES_PER_POUND;
weight = (volume + 166 - 1) / 166;
```
위 구문과 아래 구문은 같은 구문이다.
+ 매크로의 이름을 오로지 대문자로만 표기하는 것은 대부분의 C언어 프로그래머들이 지키는 암묵적인 룰이라고 할 수 있다. 전통!

### [Programming] 섭씨를 화씨로 변환하기
```
#include <stdio.h>

#define FREEZING_PT (32.0f)
#define SCALE_FACTOR (5.0f / 9.0f)

int main(void)
{
  float fahrenheit;
  float celsius;
  
  printf("Enter Fahrenheit temperature: ");
  scanf("%f", &fahrenheit);
  
  celsius = (fahrenheit - FREEZING_PT) * SCALE_FACTOR; //FREEZING_PT = 32.0f, SCALE_FACTOR = (5.0f / 9.0f)
  printf("%Celsius equivalent: %.1f\n", celsius);
  
  return 0;
}
```
```#define SCALE_FACTOR (5.0f / 9.0f)```
위 구문에서 ```(5.0f / 9.0f)```를 ```(5 / 9)```로 표기한다면 C에서는 결과 값이 0이 되버린다. 나누기를 할 때는 이 점을 유의하자.

```2-7 식별자```
프로그램을 작업하면서 변수, 함수, 매크로 등에 이름을 정해주어야 한다. 이러한 이름들을 식별자(identifier)라고 명한다.  
C에선 식별자를 정의할 때 문자, 숫자나 ```_```와 같은 밑줄 기호를 사용할 수 있지만, 숫자로 식별자를 시작할 수 없다.

예시-가능한 경우)  
```times10``` ```get_next_char``` ```_done```
예시-불가능한 경우)  
```10times``` ```get-next-char```  
```10times```의 경우 식별자 명이 숫자로 시작되고, ```get-next-char```의 경우 밑줄 기호가 아닌 뺄셈 기호를 사용하고 있다.  

C는 식별자 명에서 대ㆍ소문자를 구분하기에 유의해서 사용해야 한다.
+ C는 대소문자를 구분하기에 많은 프로그래머들이 매크로를 제외하고는 식별자를 오로지 소문자로만 작성하고, 가독성을 위해 밑줄 기호를 사용하기도 한다.

```2-8 C 프로그램의 레이아웃```  

C 프로그램은 토큰의 연속이라고 이해할 수 있다. 토큰이란 의미를 구성하는 최소 단위인데 식별자나 키워드가 토큰의 일종이다.  
+와 -와 같은 연산자나 쉼표, 세미콜론과 같은 구두점, 문자열 리터럴 등 또한 마찬가지로 토큰의 일종이다.

앞서 다뤘던 ```celsius.c``` 프로그램을 아래와 같이 스페이스를 제거할 수 있다.
```
#include<stdio.h>
#define FREEZING_PT (32.0f)
#define SCALE_FACTOR (5.0f / 9.0f)
int main(void){float fahrenheit, celsius;printf(
"Enter Fahrenheit temperature: ");scanf("%f", &fahrenheit);
celsius = (fahrenheit - FREEZING_PT) * SCALE_FACTOR;
printf("Celsius equivalent: %.1f\n", celsius);return 0;}
```
위의 코드도 ```main```함수 전체를 한 줄에 작성할 수도 있다. 전처리 지시자들은 따로 한 줄씩 배치해야하기에 모든 프로그램을 한 줄에 배치할 수는 없다.  
하지만, 프로그램을 이런 식으로 압축하는 것은 매우 지양해야할 행동이다. 스페이스가 프로그램의 가독성을 매우 높여주기 때문이다. 
또한 빈 줄은 프로그램을 논리의 흐름을 덩어리로 구분하게 해주어 독자로 하여금 구조를 쉽ㅂ게 파악할 수 있게 만들어준다.  
빈 줄없는 프로그램은 마치 목차가 없는 책을 읽는 것과 같다.

하지만 토큰 사이에 여백을 두어서는 안된다. 아래 예시를 한 번 보도록 하자.
예시)  
```fl oat fahrenheit, celsius; //*** WRONG ***```
```
fl
oat fahrenheit, celsius; //*** WRONG ***
```
예시와 같이 작성을 하게 되면 컴파일 단계에서 에러가 발생한다.
