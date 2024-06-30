# HTML include / import 하는 방법

## 자바스크립트 AJAX를 이용한 방법

### - html에 다른 html Snippet 포함하기

1. 분리하고자 하는 html 을 각각 분리하여 .html 파일 형식으로 저장한다.

ex) header.html, footer.html

https://www.w3schools.com/howto/howto_html_include.asp

![html 파일 정렬방법](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FWkkkl%2FbtsIhcEsOob%2FTCUwNwkc2Uk79bzF4NlKKk%2Fimg.png)


2. html 파일 내 include 포함한다.

index.html 파일 내

``` html
    // index.html
 
    <body>
        <div data-include-path="./layout/header.html"></div>
        <div data-include-path="./layout/footer.html"></div>
    </body>
 ```

3. include.js 파일을 생성한다.

``` js
    // include.js
 
    <script>
        window.addEventListener('load', function() {
            var allElements = document.getElementsByTagName('*');
            Array.prototype.forEach.call(allElements, function(el) {
                var includePath = el.dataset.includePath;
                if (includePath) {
                    var xhttp = new XMLHttpRequest();
                    xhttp.onreadystatechange = function () {
                        if (this.readyState == 4 && this.status == 200) {
                            el.outerHTML = this.responseText;
                        }
                    };
                    xhttp.open('GET', includePath, true);
                    xhttp.send();
                }
            });
        });
    </script>
```
 
처음 VSCode 로 할때 오른 클릭하여 Open in defalt Browser 로 열었을때는 안되었는데,
오른쪽 하단의 Go Live 버튼을 눌러 사이트를 여니 제대로 작동이 되었다.

![Go Live 버튼](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwZzeE%2FbtsIhRfnIr0%2FO4NvJOkXOLw3lbTKVtJG9K%2Fimg.png)

→ 파일 다운로드하기

https://euns420.tistory.com/entry/HTML-include-import-%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95


참고 사이트
https://velog.io/@odada/html-includeimport#html-%EB%B6%84%EB%A6%AC%ED%95%98%EA%B8%B0

https://kyung-a.tistory.com/18#1._HTML_imports
※ ↑ 위의 사이트에 다른 방법도 나와있다. 