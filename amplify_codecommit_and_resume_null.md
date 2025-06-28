# AWS Amplify CodeCommit 프로젝트 배포 오류 해결 및 일반 이력서 null 처리

## 1. Amplify로 AWS CodeCommit 프로젝트 배포 오류

### 오류 증상

Amplify 콘솔에서 CodeCommit 저장소를 클론하는 과정에서 접근 권한 오류로 인해 배포가 실패합니다.

```bash
2024-06-14T04:20:26.899Z [INFO]: # Cloning repository: https://git-codecommit.ap-northeast-2.amazonaws.com/v1/repos/new-helperit-web

2024-06-14T04:20:39.006Z [INFO]:

2024-06-14T04:20:39.131Z [INFO]: Cloning into 'new-helperit-web'...

fatal: unable to access 'https://git-codecommit.ap-northeast-2.amazonaws.com/v1/repos/new-helperit-web/': The requested URL returned error: 403

2024-06-14T04:20:39.131Z [ERROR]: !!! CustomerError: Unable to clone repository due to user error code: 128
```

### 원인

Amplify 앱에 연결된 IAM 역할에 해당 CodeCommit 저장소에 대한 `codecommit:GitPull` 권한이 설정되지 않았습니다.

### 해결 방법

1. AWS 콘솔에서 **IAM > 역할(Roles)** 로 이동합니다.
2. Amplify 앱에 연결된 역할(예: `AWSAmplifyCodeCommitExecutionPolicy-dxxxxxxxxx`)을 선택합니다.
3. **권한(Policy)** 에서 **정책 편집(Edit policy)** 을 클릭하고, JSON 탭에 다음 정책을 추가하여 리소스에 대상 저장소의 ARN을 입력합니다:

```json
{
  "Effect": "Allow",
  "Action": ["codecommit:GitPull"],
  "Resource": [
    "arn:aws:codecommit:ap-northeast-2:<AWS_ACCOUNT_ID>:new-helperit-web"
  ]
}
```

4. 정책을 저장한 후 Amplify 배포를 다시 시도합니다.

## 2. 일반 이력서 등록 시 null 처리

사업자 등록번호(`businessRegistrationNumber`) 및 사업자 등록증 파일(`businessRegistrationDocument`)이 없는 경우, 다음과 같이 `null`로 처리합니다:

```json
{
  "applicantName": "홍길동",
  "businessRegistrationNumber": null,
  "businessRegistrationDocument": null
  // 기타 필드...
}
```

- 데이터 저장 또는 API 요청 시, 해당 값이 누락되면 `null`을 명시적으로 설정하여 처리합니다.
