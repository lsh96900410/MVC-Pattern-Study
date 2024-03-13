![웹 어플리케이션 서버 구조](https://github.com/lsh96900410/aaa/assets/133841235/aaa37069-d0cd-4eed-855f-2813e8a10eb7)

Servlet은 HTTP 요청 메시지를 파싱한다. 그리고 그 결과를HttpServletRequest 객체로 제공한다.  
HttpServletRequest 객체는 HTTP 조회 및 임시 저장소 / 세션 관리 등의 역할을 제공한다.  
-> Request, Response 객체는 사용을 도와주는 것이기에, Http 스펙 자체를 이해할 수 있어야함

### MVC 
| Before | V1 | V2 |
|--------|----------|----------|
| ![MVC 1버전](https://github.com/lsh96900410/aaa/assets/133841235/3934e280-9ef1-47f0-94a1-0455973555b2)|![MVC 2버전](https://github.com/lsh96900410/aaa/assets/133841235/00a61df0-4bc1-40d1-82fa-d1bdf059072a)|![MVC 3버전](https://github.com/lsh96900410/aaa/assets/133841235/b826563f-04de-4613-9dab-797766088e19)|

### 한계 및 단점 
뷰 렌더링과 컨트롤러 작업을 분리 하였지만, 컨트롤러의 불필요하고 중복 작성 코드가 많다.

### FrontController - DispatcherServlet
클라이언트의 모든 요청을 받은 후, 요청에 알맞는 Controller 찾아서 호출  
-> Controller는 중복 코드를 제거할 수 있고, Servlet을 사용하지 않아도 됨 

| 존재 X | 존재 O |
|:--------:|:----------:|
|![프론트 컨트롤러 도입 전](https://github.com/lsh96900410/aaa/assets/133841235/b9d1a4c1-cf1d-40f5-b303-36a31ccc6ac3)|![프론트 컨트롤러 도입 후](https://github.com/lsh96900410/aaa/assets/133841235/c9aa26c2-b7f0-4cde-a57d-b47d68ec92cf)|
|**V1**|**V2**|
| FrontController 생성 | 중복 뷰 로직 분리 |
|![프론트 컨트롤러 1버전](https://github.com/lsh96900410/aaa/assets/133841235/baea69b9-f9fe-48b1-aa88-2d0ff3d056db)|![프론트 컨트롤러 2버전](https://github.com/lsh96900410/aaa/assets/133841235/8fe64c19-4856-4592-b763-b5a3f24ce418)|
|**V3**|**V4**|
| Model 객체 추가 | View Name 반환 |
|![V3](https://github.com/lsh96900410/aaa/assets/133841235/2a9984b0-18ea-408f-8c81-284f97cc5169)|![V4](https://github.com/lsh96900410/aaa/assets/133841235/83d9b523-9c7d-4a64-9ba1-d9910fe1dfe7)|
|**V5**||
| 어댑터 역할 추가 |  |
|![V5](https://github.com/lsh96900410/aaa/assets/133841235/a3151fbc-26e8-4cca-94a3-165e4ac5a96c)| |

### Spring MVC
| Self  | Framework |
|:--------:|:----------:|
|![직접 만든 스프링 MVC](https://github.com/lsh96900410/aaa/assets/133841235/2acbbbf4-d1ec-49d2-b28c-f6c55afe2c79)|![진짜 스프링 MVC 구조](https://github.com/lsh96900410/aaa/assets/133841235/a853f36b-8420-46c3-a8e5-40ba50b88a67)|

### ResponseBody
HTTP Body에 직접 반환하며, ViewResolver 대신에 HttpMessageConverter 실행  
 HttpMessageConverter : MappingJackson2HttpMessageConverter , 문자열 처리 - StringHttpMessageConverter 등 다양하다.

 ### RequestMappingHandlerAdapter
 Controller에서 사용하는 @RequestParam , Model 객체등 여러 기능이 다양한 ArgumentResolver 덕분에 사용 가능함.
 HTTP 메시지 컨버터는 1,3에 존재함.
 
| ResponseBody | RequestMappingHandlerAdapter |
|:--------:|:----------:|
| ![RESPONSEBODY](https://github.com/lsh96900410/aaa/assets/133841235/593d725e-f38f-456e-bd26-8082e7c9f32a)|![리퀘스트 매핑](https://github.com/lsh96900410/aaa/assets/133841235/afce10a5-ee69-4c16-a3ef-6921e3fc35c5)|

스프링은 대부분이 인터페이스이기에 기능 확장이 필요할 경우 WebMvcConfigurer를 상속받아서 스프링 빈으로 등록가능. 




