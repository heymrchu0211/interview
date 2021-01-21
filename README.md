## 예상 면접 질문 - 자문자답

이 문서는 제가 만약 면접을 보게 된다면 받게 될 질문들을
스스로 예상해보고 그에 대한 답변을 한 글입니다.<br>
자문자답 형식으로 작성해 보았습니다.

<br>
<br>

## position relative와 absolute의 차이점이 뭔가요?

>position속성의 값이 relative인 요소는 자기 자신이 문서 흐름상 위치해야 할 위치를 기준으로 합니다. 자기 자신을 기준으로 하기 때문에 left,top,right,bottom등의 속성을 사용하면 자기 자신의 위치를 기준으로 움직입니다. 부모중에 relative,absolute,fixed인 요소가 있어도 여전히 자기 자신을 기준으로 합니다.<br><br>
반면 position속성의 값이 absolute인 요소는 부모 요소중에 relative,absolute,fixed인 요소가 있으면 그 요소를 기준점으로 합니다.
부모중에 relative,absolute,fixed인 요소가 존재하지 않는다면 브라우저의 viewport를 기준으로 합니다. viewport란 화면에 보이는 영역을 말합니다.<br><br>
만약 요소가 div,p등의 block level 요소라고 할지라도  position속성의 값이 absolute가 되는 순간 그 요소는 더 이상 너비를 100% 차지하지 않고 마치 inline-block처럼 됩니다. 즉, 해당 요소가 갖고 있는 컨텐츠의  영역만큼 너비가 지정됩니다. 그래서 너비를 100%로 주고 싶다면 width속성의 값을 100%로 따로 지정 해야 합니다.

## rem과 em의 차이점이 뭔가요?

>먼저 rem은 html의 font-size를 기준으로 합니다. 예를 들어 html의 font-size가 20px이라고 가정한 상태에서 body요소의 font-size를 2rem으로 적용하게 되면 body요소의 font-size는 40px이 됩니다. 왜냐하면 기준이 되는 html요소의 font-size 20px 곱하기 2 = 40px이기 때문입니다. rem은 언제나 html을 기준으로 합니다.<br><br>
em은 가까운 부모 요소의 font-size를 기준으로 합니다. 예를 들어서 어떤 div요소가 있고 그의 자식으로 span요소가 있는 상황에서, div요소의 font-size가 20px이고 span요소의 font-size를 1em으로 적용하면 span요소의 font-size는 20px이 됩니다. 왜냐하면 부모인 div요소의 font-size가 기준이 되기 때문입니다.<br><br>
만약에 자신의 직계부모에 font-size가 따로 지정되어 있지 않은 경우에는 그의 부모인 조부모가 기준이 됩니다. 조부모에도 font-size가 따로 지정되어 있지 않으면 계속 부모를 타고타고 찾아 올라가다가 결국에는 html이 기준이 될 수도 있습니다. <br><br>
그런데 em은 꼭 상위요소만을 기준으로 하지 않습니다. 예를 들어서 어떤 div요소가 있고 그  div 요소의 font-size가 20px인 상황에서
그 div요소의 line-height를 1.5em으로 적용하면 line-height는 20px 곱하기 1.5 = 30px이 됩니다. 즉, 자기 자신의 font-size를 기준으로 하는 것입니다.

## opacity: 0, visibility: hidden, display:none의 차이점이 뭔가요?

>opacity 0 : 화면에서는 보이지 않지만 여전히 공간을 차지하고 있습니다. 이벤트 적용이 가능하며 tab키를 눌렀을때 해당 요소로 접근이 가능합니다.<br><br>
visibility: hidden : 화면에서는 보이지 않지만 여전히 공간을 차지하고 있습니다. 하지만 이벤트가 적용 되지 않으며 tab키를 눌렀을때 해당 요소로 접근이 불가능합니다.<br><br>
display: none : 화면에 보이지도 않고 이벤트도 적용 안되고 tab키로 진입도 할 수 없습니다.

## display가 inline 혹은 inline-block인 요소들을 배치하게 되면 요소들 사이사이에 4~5px 가량의 간격이 생기게 되는데 이 간격을 제거하려면 어떻게 해야 되나요?

몇가지의 방법이 있습니다.<br>

```html
<div class="parent">
  <span class="children">김춘영1</span><span class="children">김춘영2</span><span class="children">김춘영3</span><span class="children">김춘영4</span>
</div>
```
첫번째 방법은 html상에서 요소들을 위와 같이 개행을 하지 않고 서로 붙여 놓는 것입니다. 하지만 이렇게 하면 가독성이 너무 떨어지기 때문에 실제로 이 방법을 쓰는건 적절한 방법이 아니라고 생각합니다.<br><br>
```html
<div class="parent">
  <span class="children">김춘영1</span>
  <span class="children">김춘영2</span>
  <span class="children">김춘영3</span>
  <span class="children">김춘영4</span>
</div>
```
```css
.children {
  margin-right: -6px;
}
```
두번째 방법은 위와 같이 inline 혹은 inline-block 요소들의 margin을 음수값으로 적용 하는 것입니다. (네거티브 마진 이라고 불립니다 )  margin-right: -6px 라고 적용하게 되면오른쪽 마진은 -4px이라는 의미인데요. 이렇게 하면 요소들 사이의 간격을 없앨 수 있습니다. 하지만 정확히 말하면 없앤다기 보다는 강제로 간격을 줄인다 라고 말하는게 더 적절하다고 생각합니다.<br><br>

```css
.parent {
  font-size: 0;
}

.children {
  font-size: 1rem;
  
}
```
세번째 방법은 해당 요소들의 부모 요소의 font-size를 위와 같이 0으로 만들면 간격이 사라지게 만들 수 있습니다. 하지만 해당 요소들이 텍스트를 포함하고 있는 경우라면 font-size를 상속 받아서 해당 요소들까지도 font-size가 0이 되버립니다. 그래서 이 경우에는 해당 요소들에게 font-size를 따로 지정 해줘야 합니다.

## ir기법이 뭔가요?

ir기법이란 image replacement의 약자로서, 이미지를 볼 수 없는 사용자(화면낭독기 등의 보조기기 사용자)를 위해 이미지에 대한 대체 텍스트를 제공하는 것을 말합니다.<br> 
img요소의 alt속성과 같은 역할을 하는 것인데요. ir기법은 img요소가 아닌 css의 background-image 속성으로 이미지를 제공할때 사용하는 기법입니다.<br><br>
ir기법에 대해 설명하기 위해서 이것저것 찾아보다가 좋은 예시를 발견했는데요.<br> 바로 네이버 메인화면에 있는 검색창의 검색버튼입니다.<br><br>

![네이버 코드 이미지](https://github.com/heymrchu0211/interview/blob/main/ir-code-image-naver.png)

위 이미지를 보시면 button요소가 있고 그의 자식으로 class명이 ico_search_submit인 span요소와 class명이 blind인 span요소가 있는데요.
class명이 ico_search_submit인 span요소의 css를 보면 아래 이미지처럼 background-image가 적용되어 있는 걸 보실 수 있습니다.<br><br>

그리고 class명이 blind라고 되어있는 span요소를 보시게 되면
“검색”이라는 텍스트가 들어가있고 css는 위와 같이 적용 되어 있습니다.<br> 


이렇게 되면 화면에는 “검색”이라는 텍스트가 보이지는 않지만 화면낭독기 등의 보조기기에는 읽히게 됩니다. 
즉, ir기법은 웹접근성 준수를 위해 사용하는 것입니다.
