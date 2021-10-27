# ComputerScience
기초 컴퓨터 사이언스 지식에 대해 기록합니다.



## HTTP 개요

웹에서 이루어 지는 모든 데이터 교환에 사용되는 프로토콜 

클라이언트-서버 프로토콜 이라고도 합니다.  TCP/IP 프로토콜 기반으로 만들어진 프로토콜 입니다.

어플리케이션 레벨의 프로토콜로써, HTTP 프로토콜에서 사용하는 내용을 <u>'메시지'</u> 라고 부릅니다. 



![image-20211021163747358](./referenceImage/image-20211021163747358.png)

클라이언트에서 요청되는것을 보통 **HTTP Request** 라 하고, 서버에서의 응답을 **HTTP Response** 라고 정의 합니다. 



### HTTP Headers

#### 공통 헤더

- **Content-Type** : 해당 요청/응답에 포함되는 미디어 타입 정보 컨텐츠의 타입 및 문자 인코딩 방식을 지정

- **Content-Encoding** : 해당 개체 데이터의 압축 방식 

- **Content-Length** : 전달되는 해당 개체의 바이트 길이 또는 크기 (10진수)

  

#### 요청 헤더 (HTTP Request Type)

- **Host** : 요청하는 호스트에 대한 호스트 명 및 포트번호 (필수)
- **User-Agent** : 클라이언트 소프트웨어 명칭 및 버전 정보 
- **Cookie** : 서버에 의해 Set-Cookie로 클라이언트에게 설정된 쿠키 정보 
- **Authorization** : 인증 토큰을 서버로 보낼 때 사용하는 헤더 
- **Accept** : 클라이언트 자신이 원하는 미디어 타입 및 우선 순위를 알린다. 
- **Accept-Language** : 클라이언트 자신이 원하는 가능한 언어 
- **Accept-Encoding** : 클라이언트 자신이 원하는 문자 인코딩 방식



#### 응답헤더 (HTTP Response Type)

- **Location** : 리소스가 리다이렉트 된 때에 이동된 주소 또는 새로 생성된 리소스 주소를 명시한다. 

    				  300번대 응답이나, 201 Created 응답일 때 어느 페이지로 이동할지를 알려준다.  

- **Server** : 서버 소프트 웨어 정보 

- **Set-Cookie** : 서버측에서 클라이언트 에게 세션 쿠키 정보를 설정 

- **Allow** : 해당 엔티티에 대해 서버측에서 지원 가능한 HTTP 메소드의 리스트를 나타낸다. 

- **Access-Control-Allow-Origin** : 요청을 보내는 주소와 받는 백엔드 주소가 다르면, CORS 에러가 발생하는데 서버에서 이 헤더에 프론트주소를 적어주어야 에러가 나지 않는다. (CORS)

  `Access-Control-Allow-Origin: www.naver.com` : www.naver.com 에서 온 요청만 허용 

  `Access-Control-Allow-Origin: *` : 일일이 지정하기가 힘들다면, 모든 주소에 대해 CORS 요청을 허용하면 되지만 그만큼 보안이 취약해진다. 



- **Access-Control-Request-Method** : 지원하는 HTTP Method를 지정한다. 지정하지 않은 Method 의 응답은Method Not Allowed (405) 에러와 함께 응답한다.
- **Access-Control-Request_Headers** : 지원하는 HTTP Header 를 지정한다. 지정하지 않은 Headers 는 요청응답을 하지 않는다. 



### HTTP Message 

: 서버와 클라이언트가 HTTP 통신을 할 때 주고 받는 메시지 



### HTTP Request Message

  클라이언트가 서버에게 자료를 요청하는 Request Message 

![image-20211025180922566](C:\Users\sukang\AppData\Roaming\Typora\typora-user-images\image-20211025180922566.png)



### HTTP Response Message

서버가 클라이언트에게 받은 요청에대한 응답 메시지는 Response Message 라고 한다. 

![image-20211025180943309](C:\Users\sukang\AppData\Roaming\Typora\typora-user-images\image-20211025180943309.png)



### HTTP Body

해당 Request / Response 의 실제 메시지 / 내용으로써, Body가 없는 경우도 많다. (GET 등.)



### 요청 예시 

```http
GET /home.html HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/ *;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/testpage.html
Connection: keep-alive
Upgrade-Insecure-Requests: 1
If-Modified-Since: Mon, 18 Jul 2016 02:36:04 GMT
If-None-Match: "c561c68d0ba92bbeb8b0fff2a9199f722e3a621a"
Cache-Control: max-age=0
https://gmlwjd9405.github.io/2019/01/28/http-header-types.html
```



참조 블로그 주소 : https://gmlwjd9405.github.io/2019/01/28/http-header-types.html



### HTTP Methods  

HTTP Request Message 에 포함되는 HTTP Method 로 서버에 요청을 보낼 때 메소드를 지정한다. 

**GET** : 어떠한 데이터를 서버로 부터 획득 하고자 할 때 주로 사용하는 Method

​          데이터의 생성 / 수정/ 삭제 없이 받아오기만 할 때 사용된다. 

**POST** : 데이터를 생성/수정 할 때 주로 사용되는 Method. 데이터를 생성 및 수정 시 많이 사용 하기 때문에, 대부분의 경우 Request Body가 포함되서 전송 된다. 



**PUT** : 데이터를 수정 할 떄 주로 사용되는 Method 

**DELETE** :  데이터를 삭제 할 때 주로 사용되는 Method 

OPTIONS : 





### HTTP Status Code 

**200** (OK) : 문제없이 실행 되었을 때 서버측에서 보내는 코드 

- **201** (Created) :리소스가 정상적으로 생성 되었을 때 응답. 

- **204** (No Content) : 요청 자체는 성공 하였지만, 응답할 리소스가 없거나, 결과가 없을 때 사용한다. 404 Not Found 와 정책에 따라 혼용된다. 

  

**301** (Move  Permanently) : 해당 URI 가 다른 주소로 바뀌었을때 보내는 코드 

**400** (Bad Request) : 해당 요청이 클라이언트 단에서 잘못요청되었을 때 서버측에서 보내는 코드 요청에 포함되어야 하는 메시지나 필수 요소들이 존재하지 않거나, 지원하지 않는 요청을 수행하거나 등의 이유 일때 응답 된다 .

**401** (Unauthorized) : 요청을 수행할 권한이 없을 때 응답되는 코드 (인증 정보나, 인증 토큰이 유효하지 않거나 필요할 때)

**403** (Forbidden) : 유저가 해당 요청에 대한 권한이 없다는 뜻 

**404** (Not Found ) : 요청된 리소스가 존재하지 않거나, 없다는 응답 

**500** (Internal Server Error) : 서버에서 에러가 발생 하였을 때 사용되는 코드 





### HTTPS (Hypertext Transfer Protocol Secure)

HTTP  메시지를 암호화 화여 전송하는 Protocol 입니다. 

브라우저는 신뢰할 수 있는 사이트와 그 사이트의 공개 키를 가지고 있다. 웹브라우저가 서버에 접속 하였을 때 다음과 같은 절차를 거친다. 

- 서버는 SSL 인증서를 제공한다. 이 인증서에는 서버측의 공개키와 서비스의 정보를 담고 있다. 
- 브라우저는 이 인증서를 발급한 CA 가 자신의 CA 리스트에 있는지 확인한다. 
- 자신이 가지고 있는 리스트에 CA가 있다면 해당 공개키를 이용하여 인증서를 복호화 한다. 복호화가 된다면 이 인증서는 CA의 비공개키에 의해 암호화 되었다는 것을 알 수 있다. 
- 해당 과정이 완료 되면 (신뢰 할 수 있는 웹 사이트로 인지하고 다음과 같은 오류가 뜨지 않는다.)



![image-20211025192316272](C:\Users\sukang\AppData\Roaming\Typora\typora-user-images\image-20211025192316272.png)



### HTTP HandShakes

https://aws-hyoh.tistory.com/entry/HTTPS-%ED%86%B5%EC%8B%A0%EA%B3%BC%EC%A0%95-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-3SSL-Handshake 





## Trouble Shooting of HTTP

## Trouble Shooting

대표적인 HTTP 요청을 할 때 발생하는 문제는 다음과 같은 것들이 있습니다. 



### CORS (Cross-Origin Resource Sharing) 교차 출처 리소스 공유 : 

웹어플리케이션은 리소스가 자신의 출처 (도메인, 프로토콜, 포트) 와 다를 때 교차 출처 HTTP 요청을 실행 합니다. 

보안 상의 이유로 브라우저는 스크립트에서 시작한 교차 출처 HTTP 요청을 제한 합니다. 원칙적으로 웹어플리케이션은 자신과 동일한 출처의 리소스만 불러올 수 있으며, 다른 출처의 리소스를 불러오려면 그 출처에서 올바른 CORS 헤더를 포함한 응답을 반환 해야 합니다. 

CORS 문제는 브라우저 에서, Javascript XMLHttpRequest 와 Fetch API 호출 시 해당 CORS 문제 발생 가능 



#### 출처가 다른 것이 무엇일까? 

: 출처가 다르다고 함은, Protocol, Host, 포트번호 까지 모두 합친 것을 의미하며, 서버의 위치를 찾아가기 위해 필요한 가장 기본적인 것의 묶음이라고 볼 수 있습니다. 따라서, 해당 정보 중 어느 하나가 다르다고 하면, 출처가 다르다고 할 수 있습니다. 

![image-20211021185421217](./referenceImage/image-20211021185421217.png)



CORS 문제가 발생 하게 되면, API 서버 로직에서 이를 처리해 주어야 합니다. 언어별로 처리해주는 방법은 각각 다르나, C# (ASP.NET Core / ASP.NET ) 에서는 아래와 같이 지원할 수 있습니다. 



**Case : ASP.NET Core 에서 CORS 지원 하기.** 

```c#
          
/* ASP.NET Core Startup.cs 에 다음 내용 추가*/
services.AddCors(options =>
            {
                options.AddPolicy("CORS Configuration", builder =>
                {
                    builder.AllowCredentials() 
                           .AllowAnyHeader() // 어떤 HTTP Header 도 허용한다. 
                           .AllowAnyMethod(); // 어떤 HTTP Method 도 허용한다. 
                });
            });

```

**Case : ASP.NET 에서, CORS 지원 하기** 

관련 링크 : https://docs.microsoft.com/ko-kr/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api 

```c#
using System.Web.Http;
namespace WebService
{
    public static class WebApiConfig
    {
        public static void Register(HttpConfiguration config)
        {
            // New code
            config.EnableCors();

            config.Routes.MapHttpRoute(
                name: "DefaultApi",
                routeTemplate: "api/{controller}/{id}",
                defaults: new { id = RouteParameter.Optional }
            );
        }
    }
}
```



**Case : Controller 로직에서 지원하기**

```c#
[EnableCors(origins: "http://www.example.com", headers: "*", methods: "get,post")]
public class TestController : ApiController
{
    public HttpResponseMessage Get() { ... }
    public HttpResponseMessage Post() { ... }
    public HttpResponseMessage Put() { ... }    
}

[EnableCors(origins: "*", headers: "*", methods: "*", exposedHeaders: "X-Custom-Header")]
public class TestController : ApiController
{
    public HttpResponseMessage Get()
    {
        var resp = new HttpResponseMessage()
        {
            Content = new StringContent("GET: Test message")
        };
        resp.Headers.Add("X-Custom-Header", "hello");
        return resp;
    }
}
```



출처 : https://developer.mozilla.org/ko/docs/Web/HTTP/Overview



### HTTP DEBUGING

웹 어플리케이션 / API 서버를 개발 할 때에 가장 많이 사용하게 되는 디버깅 방법을 알아보자. 



#### Fiddler 를 통한 HTTP Message 캡쳐 

웹 어플리케이션, API 서버를 구현 할 때에 디버깅 용도로 Fiddler 가 많이 사용된다. 실제로 요청이 나갔는지, 어떻게 요청을 하고 있는지 응답을 어떻게 받았는지를 먼저 파악하고, 디버깅 하는데 활용 할 수 있다. 

![image-20211027155216033](C:\Users\sukang\AppData\Roaming\Typora\typora-user-images\image-20211027155216033.png)





**HTTP Request Message Example** 

1. 요청이 GET / POST 일 경우 실제로 요청된 Request Message 가 프로그램에서 의도한 Request Message가 맞는지 확인한다. 

2. POST 일 경우, 메시지 요청 시 Body String 이 있다면 그 Message 도 확인이 필요하다. 

3. 인증이 필요한 서비스 일 경우 헤더에 인증키가 제대로 들어가 있는지 확인한다. 

   

``` http
GET http://dev-phrkids-api.ubware.com/api/patients/6181D2285F71288DDB1C3D2C539D31140B779DF17AC40460125EC0BA6DD90016/prescriptions/2 HTTP/1.1
Host: dev-phrkids-api.ubware.com
Connection: keep-alive
access-control-allow-origin: *
accept: application/json
hspt-key: EB705BA10928085CAE5EE9F60A26C7EF780463665F8CE4C8BFEFE1C19099C99D
DNT: 1
service-key: ubcare-phrkids-test
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.54 Safari/537.36
Origin: http://dev-phrkids.ubware.com
Referer: http://dev-phrkids.ubware.com/
Accept-Encoding: gzip, deflate
Accept-Language: ko-KR,ko;q=0.9

```



**HTTP Response Message Example** 

1. Status Code 를 확인하여 정확히 어떤 상태인지 진단한다. 
   - 200 OK : 정상 
   - 404 NotFound : 잘못된 경로로 요청하지는 않았는지? 해당 조건에 해당하는 리소스가 없는 것인지? 
   - 400 BadRequest : 잘못된 요청을 보내지는 않았는지 (필수 속성 누락 등)
   - 401 Not Authorized : 인증 정보 누락 , 만료 
   - 500 Internal Server Error : 서버 에러 발생 
2. Content-Type 확인 : Content-Type 확인 하고, 실제 처리 로직에서 해당 Content-Type으로 Message 가 처리되고 있는지 확인 필요. 
3.  Message 구조를 확인 하여, Deserialize 하여, 객체화 하여 사용하고 있다면 Deserialization 시 객체의 속성의 자료형 및 속성 이름이 일치하는지 확인 

```Http
HTTP/1.1 200 OK
Cache-Control: no-cache
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Server: Microsoft-IIS/10.0
Access-Control-Allow-Origin: *
X-AspNet-Version: 4.0.30319
X-Powered-By: ASP.NET
Date: Wed, 27 Oct 2021 06:51:43 GMT
Content-Length: 9513

{"Result":{"PrescriptionOrderIdx":30,"ManagementCode":20,"StartDate":"2021-09-23T00:00:00","EndDate":"2021-09-27T00:00:00","SCORAD":[],"VAS":[],"Bristol":[] ...
```





#### Fiddler 를 통한 패킷 재사용 

변경 테스트





## RESTful



## HTTPS HandShake



## WAS vs WebServer



## Cookie 



## Session 



## Local Storage / Session Storage 



## CORS



## 브라우저 렌더링 과정



### 브라우저는 어떻게 동작하는가? - 탈리 가르시엘 - 

번역본 :  https://d2.naver.com/helloworld/59361

원글 : https://www.html5rocks.com/en/tutorials/internals/howbrowserswork/ 



## JavaScript



### 이벤트 버블링 / 캡쳐링 / 이벤트 위임

https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/

출처 : 캡틴 판교 github



### Vue.js 개발을 위한 주요 ES6 문법 4가지

https://joshua1988.github.io/web-development/translation/essential-es6-features-for-vuejs/

출처 : 캡틴 판교 github



### 간단히 훑어보는 자바스크립트 기본기 다지기

https://joshua1988.github.io/web-development/javascript/javascript-basic-summary/

출처 : 캡틴 판교 github



### Javascript 면접 질문 

https://joshua1988.github.io/web-development/javascript/javascript-interview-3questions/ 

출처 : 캡틴 판교 github