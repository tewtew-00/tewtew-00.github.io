_includes/anchor_headings.html

#### 기능 
각 제목을 링크 가능한 목적지로 만들어주는 기능
(해당 링크를 복사하면 링크를 공유했을 때 글의 바로 그 위치로 이동해올 수 있음)

#### 기능(심화)

마크다운으로 작성된 HTML 콘텐츠의 모든 제목(h1-h6)에 자동으로 앵커 링크를 추가해주는 Jekyll 플러그인. 

#### 전체 구조 이해 

Jekyll의 Liquid 템플릿 언어로 작성됨 
Jekyll은 정적 사이트 생성기 
Liquid는 템플릿 엔진
    템플릿 = 빈칸이 있는 양식 
    엔진 = 무언가를 동작시키는 핵심 부품(연료)
    -> 템플릿 1개 + 데이터만 바꿔서 무한대 페이지 생성!
-> 템플릿 엔진 = 템플릿 + 데이터를 합쳐서 완성된 HTML을 만들어주는 프로그램 

##### Liquid 템플릿 엔진 예시 

**기본 문법**
변수 출력 
```liquid
    안녕하세요 {{ user.name }}님!
    오늘은 {{ today }}입니다. 
```

조건문
```liquid
    {% if user. age >= 20 %}
        성인입니다. 
    {% else %}
        미성년자입니다. 
    {% endif %}

반복문 
```liquid
    <ul>
    {% for item in shopping_list %}
        <li>{{ item }}</li>
    {% endfor %}
    </ul>

**실제 변환 과정**

1단계: 템플릿 작성 
```liquid
    <h1>{{ site.title }}</h1>
    <p>작성자: {{ author }}</p>
    {% if posts.size > 0 %}
        <ul>
        {% for post in posts %}
            <li><a href="{{ post.url }}"</li>
        {% endfor %}
        </ul>
    {% endif %}
```

2단계: 데이터 준비 
```yaml
    site: 
        title: "내 블로그"
    author: "김철수"
    posts: 
        - title: "첫 번째 글"
          url: "/post1"
        - title: "두 번째 글"
          url: "/post2"
```
        
3단계: 엔진이 변환(자동)
```html
<h1>내 블로그</h1>
<p>작성자: 김철수</p>
<ul>
    <li><a href="/post1"></a></li>
    <li><a href="/post2"></a></li>
</ul>
```

