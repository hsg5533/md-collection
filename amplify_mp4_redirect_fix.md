# Amplify로 배포한 웹에서 mp4 영상이 나오지 않을 경우

AWS Amplify로 MP4 영상을 적용한 웹을 배포할 경우, 영상이 정상적으로 출력되지 않는 문제가 발생할 수 있습니다.

## 원인

기본적으로 Amplify에 설정된 리디렉션 규칙이 MP4 확장자를 포함하지 않기 때문입니다.  
기본 리디렉션 설정 예시:

```plaintext
</^[^.]+$|.(?!(css|gif|ico|jpg|js|png|txt|svg|woff|ttf|map|json)$)([^.]+$ )/>
```

## 해결 방법

MP4 확장자를 허용하도록 리디렉션 규칙에 `mp4`를 추가합니다:

```plaintext
</^[^.]+$|.(?!(css|gif|ico|jpg|mp4|js|png|txt|svg|woff|ttf|map|json)$)([^.]+$ )/>
```

이제 MP4 영상 파일이 정상적으로 로드됩니다.
