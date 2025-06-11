+++
title = 'AI와 클린코드'
date = 2025-06-02T23:32:57+09:00
draft = false
+++
첫 포스팅 주제를 고민하던 중, 문득 개발자라면 누구나 써봤을 Chat GPT, Gemini 같은 AI 툴에 대한 이야기가 떠올랐습니다. 사실 저는 지금까지 AI 도구를 사용하지 않고 개발을 해본 적이 없을 정도로 AI에 익숙한 편인데, 오히려 그렇기 때문에 AI에 대한 경계를 늦추지 않으려 노력하고 있습니다. 이번 글에서는 프로젝트를 진행하면서 사용했던 AI 도구 활용 경험과 클린코드를 작성하기 위해 활용하는 기능을 이야기해보고자 합니다.  

---

### 첫 번째 프로젝트  
서툴지만 열정은 있었던 ~~ㅋㅋ~~ 첫 번째 프로젝트에서 사용했던 AI는 바로 **Locofy.ai**였습니다.
Figma의 플러그인으로 처음 접했는데, UI 디자인을 넘기면 바로 다양한 프로그래밍 언어로 코드 변환을 해주는 도구입니다. 뭔가 빠르게 결과물을 만들어주긴 하는데 막상 코드를 들여다보면 효율성이라고는 전혀 없는 👽alien code👽에 가까웠습니다. 이걸 사용하기 편하게 가공하는 작업이 필요했고, 나중엔 직접 코드를 작성할 걸 하는 후회가 들기도 했습니다.  

[Locofy.ai](https://www.locofy.ai/) 웹사이트에 오랜만에 들어가 보니 생각보다 많은 곳에서 사용되고 있었습니다...?
얼마나 바뀌었나 테스트해보고 싶어서 Figma로 다시 변환해 보려 했는데, 1년 전만 해도 무료였던 서비스가 지금은 다 유료로 바뀌어서 아쉽게도 다시 변환하는 건 포기했습니다. 유료는 조금 다른가..?  

![Locofy](/img/first-project.png)  
이땐 S3나 Tailwindcss를 잘 몰라서 그냥 퍼블릭 폴더에 사진을 다 때려 박고 외부 css 파일을 사용했습니다. 그런데 Locofy가 클래스명을 container1, div1 이런 식으로 짜줘서 겹치는 클래스명이 많았고 css가 깨지는 문제가 발생했습니다.  

```css
.kiosc_p24 {
  margin: 0;
  position: absolute;
}
.kiosc_p24 {
  top: 71px;
  left: 106px;
  color: var("--color-gray-100");
}
.kiosc_p25 {
  margin-left: 14px;
  display: flex;
}
```  
결국 위 예시처럼 클래스명 앞에 어떤 페이지인지 이름을 다 달아줬는데 그것 또한 하나하나 직접 고쳤던 기억이 있습니다. 하루 종일 클래스명을 수정하면서 AI에 대한 불신이 조금 생겼던 것 같습니다.😅 이걸 어떻게 써? 하는 생각..?  

---

### 두 번째 프로젝트  
두 번째 프로젝트 개발 기간에는 기한 내에 완료해야 한다는 압박감에 코드의 질은 크게 생각하지 않았던 것 같아서 개인적으로 아쉬움이 많이 남습니다. 이때 처음으로 GPT 유료 버전을 사용해 보았는데 무료 버전이 뚝뚝 끊겨서 불편한 점을 제외하고는 크게 메리트가 있는지 잘 모르겠습니다.

\+ 그리고 최근 들어 GPT의 답변이 과도하게 긍정적인 느낌이 나서 Gemini와 병행하며 사용하던 중 재미있는 읽을거리를 발견했습니다. 메일링 서비스를 여러 곳에서 받고있는데, 요즘IT라는 곳에서 접하게 된 내용입니다.  

[🔗 아첨꾼이 된 GPT '롤백'한 오픈AI: 우리가 아첨에 대해 놓친 것 ](https://yozm.wishket.com/magazine/detail/3114/?data=DyidTbW5YqJ54kW7MmKRjUBUv%20mAv8hjI1PQqaJBw48%3D&source=daily_latest_news)  


---  

다양한 AI 도구를 사용하며 겪었던 시행착오 덕분에 이후 개인, 팀 사이드 프로젝트를 진행할 때는 단순히 빠르게 결과물을 만드는 것보다 코드의 질과 설계 방식에 더 깊이 있는 고민을 하게 되었습니다. 이는 궁극적으로 클린하고 유지 보수하기 쉬운 코드를 작성하는 것을 목표로 삼게 된 계기가 되었습니다.

JetBrain의 IntelliJ를 사용 중인데, 코드를 작성하면 중복되는 코드, 에러가 발생할 만한 코드, 더 좋은 방향으로 개선할 수 있는 코드에 경고⚠️가 발생합니다.  

<div class="intelliJ-box">
    {{< figure src="/img/intellij1.png" alt="IntelliJ1" class="intelliJ1" >}}
    {{< figure src="/img/intellij2.png" alt="IntelliJ2" class="intelliJ2" >}}
</div>


경고창을 마우스 우클릭하면 창이 하나 뜨는데,  

![IntelliJ3](/img/intelliJ3.png)  

바로 해결할 수 있게 고쳐주기도 하고(항상 해결책이 뜨는 것은 아님) 경고 메시지를 복사할 수도 있습니다.
버전 업데이트로 코드 작성 방식이 달라져서 GPT나 Gemini한테 아무리 물어봐도 해결책을 찾지 못할 때,
*Show Quick-Fixes*를 누르면 쉽게 해결되는 경우도 더러 있습니다.

물론 다른 글들을 읽어보면 이 경고가 거슬려서 특정 경고만 안 나타나게 설정하는 방법도 알려주고 하지만,
아직 저는 이게 해결해야 하는 경고인지, 넘어가도 되는 경고인지 판단하는 능력이 부족해서 그냥 내버려두고 있습니다.

가장 최근에 이 기능 때문에 해결했던 예시를 들자면,
테스트 코드 작성을 위해 **스프링 문서**를 보면서 따라 하고 있었을 때입니다.  

```java
@WebMvcTest(GreetingController.class)
class WebMockTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean // 🚨에러 발생 위치
    private GreetingService service;

    @Test
    void greetingShouldReturnMessageFromService() throws Exception {

        when(service.greet()).thenReturn("Hello, Mock");

        this.mockMvc.perform(get("/greeting")).andDo(print()).andExpect(status().isOk())
                .andExpect(content().string(containsString("Hello, Mock")));

    }

}
```  

분명 문서 그대로 작성했는데도
'org.springframework.boot.test.mock.mockito.MockBean' is deprecated since version 3.4.0 and marked for removal이라는 에러가 발생했습니다. 에러 메시지만 봐도 알 수 있지만, 버전 업데이트가 되면서 테스트 클래스에 의존성 주입을 위해 사용했던 @MockBean 어노테이션이 Deprecated 되고 @MockitoBean을 사용해야 한다는 사실을 알게 되었습니다.

이러한 경험들을 통해 습관이 하나 생겼습니다.
커밋 하기 전에 경고가 얼마나 있는지, 해결할 수 있는 경고인지, 해결할 수 있으면 그 코드를 조금이라도 더 보기 좋게 작성할 수는 없는지 고민하고 커밋을 한다는 것입니다. ~~그렇게 대단한 건 아니지만 나름 도움 됨..~~  

---  

### **마치며**  
AI 도구가 개발 생산성을 높이는 강력한 도구이긴 하지만, 개발자 스스로의 코드 품질과 설계 역량이 무엇보다 중요하다는 걸 잊지 않고, AI를 현명하게 활용하며 더욱 좋은 코드를 작성하기 위해 꾸준히 노력해야 할 것 같습니다.