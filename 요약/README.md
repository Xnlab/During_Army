왜 새로이 시작하는가,,, 

http://sunyzero.tistory.com/225
위의 글을 본 나는 엄청난 충격에 빠졌다.
내가 여태껏 해오던 C가 사파의 무공이였다니,,, 내 나이 22 지금이라도 늦지 않았으니 다시 시작할 예정이다.

그러한 기념으로 오늘의 위의 글을 내 나름대로 정리해보는 시간을 갖고자 한다.

---------------------------------------------------------------------------------------------------
C언어는 문법이 굉장히 적지만 절대로 쉽지 않다. 그 이면에 속아 C가 쉽다고 생각하지 말아라.
사파에서는 '포인터'를 C의 장벽이라고들 설명하지만, 본질은 그게 아니다. 그 너머에 있는 실제로 활용하는 분야.
즉, 운영체제, 하드웨어, 네트워크가 어우러지는 세계에 비하면 우주의 먼지와 같다고 할 수 있다.
그러므로, 운영체제, 하드웨어, 네트워킹을 같이 배워야 C를 제대로 배울 수 있다.

질문0. C언어는 언제, 어디서, 누가, 무엇을 위해 만들었는가?
질문1. C언어 국제표준(ISO/IEC 9899)은 무엇이며 C99, C11은 무엇인가?
질문2. C언어의 stdio(표준입출력)는 왜 만들어졌는가?
질문3. 전처리기(preprocessor)가 하는 일은 무엇인가? 그리고 왜 만들어졌는가?
질문4. long, int, short, pointer 변수의 크기는 몇 bit인가? (이들 크기는 고정 사이즈가 아님. int는 32bit라고 단정하면 틀린 거다)
질문5. API와 ABI는 무엇인가?
질문6. 오브젝트(object)란 무엇인가? (객체지향의 오브젝트를 말하는 것이 아님)
질문7. 링커(linker)가 하는 일은 무엇인가?
질문8. call-by-reference, call-by-value란 무엇인가? (C에 왜 call-by-reference가 없는지 설명할 수 있어야 함)
질문9. C언어의 main 함수의 return 값은 왜 int 인가? (void main()으로 선언하면 왜 틀리는가?)
질문10. C언어와 C++은 다른 하나가 부분집합인 서브셋인가? 아니면 둘은 다른 언어인가?
질문11. 하드웨어 제어에 C언어가 사용되는 이유는 무엇인가?
질문12. 시퀀스 포인트(sequence point)가 무엇인가?
질문13. Side effect란 무엇인가?
질문14. UB(Undefined behavior)란 무엇인가?

위 질문에 절반도 모른다면 C언어를 제대로 배웠다고 할 수 없다. 만약 당신이 제대로 배운 것이 아니라면 상단의 링크로 들어가 한 번 정독해보기를 바란다.

켄 톰슨, 데니스 리치, 브라이언 커니한이 누굴까 + Bill Joy, Richard Stallman
켄 톰슨 : C언어의 모체인 'B'언어를 개발, PDP-7로 게임을 하려다 돌아가지 않는 운영체제를 보고 화가난 그는 운영체제를 개발하기로 한다.
그 운영체제가 모든 것의 시작점인 '유닉스'이다. 또한 켄 톰슨이 객원교수로 있으면서 빌 조이 등과 개발한 BSD는 리눅스의 기원이 됐다.
BSD : 유닉스로 만든 운영체제로 리눅스의 기원
데니스 리치 : 켄 톰슨과 함께 C언어와 유닉스 시스템을 개발했고, 브라이언 커니한과 'The C Programming Language'를 출판했다.
리차드 스톨만 : GNU창설자로 소프트웨어 저작권을 없애자는 자유 소프트웨어 운동을 지향했다.

C언어를 입문하는 단계에서는 IDE 사용을 비추한다. gcc나 clang을 직접 사용해 프리프로세싱, 컴파일, 링킹이 어떻게 작동하는지 이해해야한다.

끝으로 필자는 23-02-06을 기점으로 위키독스의 올라와 있는 주민하님의 KNK를 통해 C언어의 기본부터 공부하여 깃허브에 올릴 생각이다.
끈기, 열정, 노력을 통해 KNK의 내용과 예제, 연습문제를 부디 깃허브에 모두 올릴 수 있으면 좋겠다!
