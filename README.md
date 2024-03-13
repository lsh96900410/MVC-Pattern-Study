![웹 어플리케이션 서버 구조](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/5dab9cf4-e8f6-4f1f-99da-a23e72851ca5)

Servlet은 HTTP 요청 메시지를 파싱한다. 그리고 그 결과를HttpServletRequest 객체로 제공한다.  
HttpServletRequest 객체는 HTTP 조회 및 임시 저장소 / 세션 관리 등의 역할을 제공한다.  
-> Request, Response 객체는 사용을 도와주는 것이기에, Http 스펙 자체를 이해할 수 있어야함

### MVC 
| Before | V1 | V2 |
|--------|----------|----------|
| ![MVC 1버전](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/bd7a4d72-5d4e-4db2-a3aa-63b90de9c9ef)|![MVC 2버전](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/e3add8c7-9f55-4d6b-8e31-267da3e2d65a)|![MVC 3버전](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/3c7febc5-e6ba-4559-8cfe-66e006088251)|

### 한계 및 단점 
뷰 렌더링과 컨트롤러 작업을 분리 하였지만, 컨트롤러의 불필요하고 중복 작성 코드가 많다.

### FrontController - DispatcherServlet
클라이언트의 모든 요청을 받은 후, 요청에 알맞는 Controller 찾아서 호출  
-> Controller는 중복 코드를 제거할 수 있고, Servlet을 사용하지 않아도 됨 

| 존재 X | 존재 O |
|:--------:|:----------:|
|![프론트 컨트롤러 도입 전](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/aaeb49b6-fc9a-4ff6-b4eb-fcef37a89d04)|![프론트 컨트롤러 도입 후](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/4c82aaa6-3258-4b03-898f-ddd1833fd67f)|
|**V1**|**V2**|
| FrontController 생성 | 중복 뷰 로직 분리 |
|![프론트 컨트롤러 1버전](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/4b9c09f7-344b-4c3b-935d-04526638d355)|![프론트 컨트롤러 2버전](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/1c7297e4-83f8-460e-9e90-5ad5786728e4)|
|**V3**|**V4**|
| Model 객체 추가 | View Name 반환 |
|![V3](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/15fd68fe-7960-4164-a520-40a3c5cd4406)|![V4](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/58e055aa-7f5b-47ee-b9ba-0b1bf52473e6)|
|**V5**||
| 어댑터 역할 추가 |  |
|![V5](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/a6ffffb2-6f1a-44f0-bf81-1782b78cc13b)| |

### Spring MVC
| Self  | Framework |
|:--------:|:----------:|
|![직접 만든 스프링 MVC](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/d444073a-5abc-4f7a-b97b-86c0b32f799e)|![진짜 스프링 MVC 구조](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/837b1a4f-db2a-4cd2-99ca-e6f07c64a754)|

### ResponseBody
HTTP Body에 직접 반환하며, ViewResolver 대신에 HttpMessageConverter 실행  
 HttpMessageConverter : MappingJackson2HttpMessageConverter , 문자열 처리 - StringHttpMessageConverter 등 다양하다.

 ### RequestMappingHandlerAdapter
 Controller에서 사용하는 @RequestParam , Model 객체등 여러 기능이 다양한 ArgumentResolver 덕분에 사용 가능함.
 HTTP 메시지 컨버터는 1,3에 존재함.
 
| ResponseBody | RequestMappingHandlerAdapter |
|:--------:|:----------:|
| ![RESPONSEBODY](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/26b3bd94-9f21-458e-97d2-75c29d37540d)|![리퀘스트 매핑](https://github.com/lsh96900410/Servlet-MVC-Study/assets/133841235/2e4f0035-0b65-4c08-82cc-6077be1021f1)|

스프링은 대부분이 인터페이스이기에 기능 확장이 필요할 경우 WebMvcConfigurer를 상속받아서 스프링 빈으로 등록가능. 




