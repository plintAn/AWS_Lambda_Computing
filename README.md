# AWS_Lambda_Computing
AWS Lambda를 사용하여 사용자 질문에 "예", "아니요" 또는 "아마도"라고 대답하는 "Fortune Teller" 애플리케이션을 만듭니다

AWS 미니 프로젝트를 생성 및 배포한 다음 API 게이트웨이 게이트웨이를 사용하여 운세 웹 애플리케이션을 대중에게 공개하는 방법을 배우게 됩니다


### 1단계: AWS Lambda 함수 설정
- AWS Management Console을 열고 Lambda 서비스로 이동합니다.
- "기능 만들기"를 클릭하고 "처음부터 작성"을 선택하세요.
- 함수 이름을 입력하고 런타임(예: Python 3.8)을 선택합니다.
- "함수 코드"에서 무작위 응답을 생성하는 코드를 작성하거나 업로드하세요.
- 메모리, 타임아웃, 실행 역할 등의 기능 설정을 구성합니다.

### 2단계: 점술 코드 작성
- Python에서 무작위 모듈을 가져옵니다.
- 1과 3 사이의 임의의 정수를 생성하는 함수를 정의합니다.
- 조건문을 사용하여 무작위 정수를 응답에 매핑합니다(예: 1 = "예", 2 = "아니요", 3 = "아마도").
- 응답을 Lambda 함수의 출력으로 반환합니다.

```python
import json
import random

def random_integer():
    options = [1, 2, 3]
    return random.choice(options)

def lambda_handler(event, context):
    option = random_integer()
    
    if option == 1:
        value = "yes"
    elif option == 2:
        value = "no"
    else:
        value = "may be"
    
    message = value
    
    return {
        'statusCode': 200,
        'body': json.dumps(message)
    }

```

### 3단계: API 게이트웨이 설정
- AWS 콘솔에서 API Gateway 서비스를 엽니다.
- "API 생성"을 클릭하고 "HTTP API"를 선택합니다.
- 경로, 방법(예: GET) 및 통합 유형(Lambda 함수)을 정의합니다.
- 앞서 생성한 Lambda 함수를 선택합니다.
- 필요에 따라 요청 및 응답 설정을 구성합니다.

매개변수 세팅

![image](https://github.com/plintAn/AWS_Lambda_Computing/assets/124107186/0300bd45-ddce-4b4e-a929-26a8e6c0b8d9)



### 4단계: 코드 배포
- API Gateway 콘솔에서 "배포"를 클릭한 다음 "생성"을 클릭합니다.
- 단계(예: "prod")를 선택하고 API를 배포합니다.
- 사용자가 점쟁이에 액세스하는데 사용할 API 엔드포인트 URL을 복사합니다.

![image](https://github.com/plintAn/AWS_Lambda_Computing/assets/124107186/beeb6765-8270-4e37-b082-29104d4c33a5)


### 5단계: 코드 테스트
- Postman과 같은 도구나 브라우저를 사용하여 API 엔드포인트에 GET 요청을 보냅니다.
- 각 질문에 대해 "예", "아니요" 또는 "아마도"라는 응답을 받았는지 확인하십시오.
- 응답의 무작위성을 보장하기 위해 다양한 질문으로 테스트합니다.

Output

![AWS_Lambda_computing1](https://github.com/plintAn/AWS_Lambda_Computing/assets/124107186/00b4374f-f73f-447f-adad-aef08c6bef23)

결과는 다음과 같았고, 이를 통해 랜덤으로 반환하


이렇게 해서 AWS Lambda 및 API Gateway를 사용하여 사용자 질문에 응답하는 Fortune Teller 애플리케이션을 구축했습니다

### 배운점

이 프로젝트에서는 AWS Lambda와 API Gateway를 사용하여 "Fortune Teller" 애플리케이션을 만들었는데, 사용자가 질문하면 Lambda 함수가 무작위로 "예", "아니요", "아마도"를 반환합니다. 이를 통해 AWS 서비스를 활용하고 서버리스 애플리케이션을 개발하는 방법을 배웠습니다.
