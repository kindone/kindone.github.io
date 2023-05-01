---
title: 다이어그램의 활용
---
# 다이어그램으로 생각을 표현하기

생각을 잘 발전시키기 위해서 생각을 우선 잘 표현하는 것이 중요하다.

물론 때로는 생각이 구체적인 형태로 표현하기 위한 준비가 부족한 경우도 있다. 하지만 어떤 생각이 머릿 속에 분명히 자리 잡았는데도 누군가에게 그 생각을 온전히 전달하기 위한 형태로 표현할 수단이 마땅치 않은 경우는 아쉬움이 남는다.

자신의 생각을 정확하게 표현하는 것은 경우에 따라 불가능하기도 하다. 고도로 훈련된 그래픽 디자이너나 화가가 아닌 이상 머릿속의 이미지를 그대로 표현하기는 어려울 것이다. 언어적 능력이 탁월하지 않다면 글로 표현하는 것도 한계가 있을 것이다.

<figure markdown>

<img src="/images/input.png" height="148" />

</figure>

소프트웨어 기술은 많은 발전을 이뤘지만 많은 사람들에게 여전히 아날로그 방법론이 생각을 표현하는데 가장 강력한 수단으로 여겨진다.
펜이나 마커를 가지고 대충 끄적이는 행위는 놀랍도록 생각을 잘 표현할 수 있는 방법이다.

컴퓨터나 스마트폰으로는 글자를 입력하는 것은 상당히 효과적이다. 키보드를 잘 사용한다면 일반적으로 말보다는 다소 느리지만 펜으로 적는 것보다는 훨씬 빠르게 생각을 나타낼 수 있다. 하지만 컴퓨터로 글자 이외의 것을 표현하려는 경우 그 불편함은 급속도로 증가한다.

아날로그 도구들을 디지털 세계로 그대로 가져 오려는 시도로는 디지타이저 기술이 있는데 대표적으로 Apple Pencil이나 삼성의 S펜 같은 태블릿 전용 펜 등이 있다. 종이에 적은대로 디지털 신호로 저장해주는 스마트 펜과 같은 도구를 이용할 수도 있다. 이들은 모두 디지털 화면에 아날로그적 방식으로 끄적이는걸 가능하게 한다[^digitizing].

## Text-to-diagram 마크업 언어

오직 글자를 입력하는 방식을 선호한다면 위 그림처럼 다이어그램 도구를 사용할 수 있다. 위 다이어그램은 [`D2`](https://d2lang.com/)라는 다이어그램 언어로 작성했다. 다음처럼 Markdown의 코드 블럭을 이용해서 다이어그램을 삽입할 수 있다.


````md title="위 그림의 D2 코드"

"Analog": {
  "Jotting down with pen"
}

"Digital": {
  "Typing with keyboard"
}

````

개발자들이 많이 사용하는 Github에서 기본 다이어그램으로 정착된 [`mermaid`](https://mermaid.js.org)도 있고 Graphviz 등 다양한 종류의 다이어그램 언어들이 존재한다.


=== "이미지"
    <figure markdown>

    ```kroki-nomnoml
#stroke: #555866
#fill: #cfcfcf;#cfcfcf
#lineWidth:2

    [다이어그램 마크업 언어|
        [mermaid|Github에서 사용]
        [graphviz]
        [D2]
        [nomnoml|이 그림을 그린 언어]
        [PlantUML]
        [Pikchr]
        [...]
    ]
    ```
    </figure>

=== "nomnoml 코드"

    ```md
    #stroke: #555866
    #fill: #cfcfcf;#cfcfcf
    #lineWidth:2

    [다이어그램 마크업 언어|
        [mermaid|Github에서 사용]
        [graphviz]
        [D2]
        [nomnoml|이 그림을 그린 언어]
        [PlantUML]
        [Pikchr]
        [...]
    ]
    ```

아래 다이어그램은 다이어그램 언어가 이미지로 보여지는 과정을 간략하게 나타내고 있는데 [`PikChr`](https://pikchr.org)라는 다이어그램 언어로 만들었다[^pikchr].


=== "이미지"
    <figure markdown>
    ```kroki-pikchr
    arrow right 200% "다이어그램이 포함된" "markdown"
    box rad 10px "Markdown" "포매터" fit
    arrow right 200% "HTML+SVG" ""
    arrow <-> down from last box.s
    box same "다이어그램" " 트랜스파일러 " fit
    ```{ width="360" }
    </figure>

=== "Pikchr 코드"

    ```md
    arrow right 200% "다이어그램이 포함된" "markdown"
    box rad 10px "Markdown" "포매터" fit
    arrow right 200% "HTML+SVG" ""
    arrow <-> down from last box.s
    box same "다이어그램" " 트랜스파일러 " fit
    ```


다양한 다이어그램 마크업 언어들을 통합해서 제공하는 [`Kroki`](https://kroki.io)라는 것도 있다. `Kroki`는 위에 언급된 몇가지 다이어그램 도구들을 통합해서 트랜스파일해주는 서비스를 제공해주고 원한다면 Docker 컨테이너를 이용해서 자체 로컬 환경에서 다이어그램을 트랜스파일할 수 있도록 해준다[^kroki].

[^digitizing]: 하지만 끄적인 내용을 다른 텍스트에 자연스럽게 삽입하는 워크플로우를 제공하는 소프트웨어는 그리 많지 않은 것 같다.
[^pikchr]: Pikchr는 상대 좌표계상의 위치를 지정해야 하기 때문 높은 수준의 제어를 가능하게 하지만 문법이 조금 더 복잡한 편이다.
[^kroki]: 다양한 다이어그램 언어를 혼용할 경우 각 다이어그램 언어가 이미지로 변환되는 실행 환경이 다르기 때문에 이들 환경을 각각 구축해야 하는 번거로움이 있다. Kroki가 이 경우에 빛을 발한다.