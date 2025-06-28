# iOS 네이버 & 카카오 로그인 오류 해결

iOS 환경에서 네이버 및 카카오 로그인 기능이 동작하지 않을 때, `AppDelegate.mm` 파일에 아래 코드를 추가하여 문제를 해결할 수 있습니다.

```objc
#import <NaverThirdPartyLogin/NaverThirdPartyLoginConnection.h>
#import <RNKakaoLogins.h>

- (BOOL)concurrentRootEnabled
{
  return true;
}

- (BOOL)application:(UIApplication *)application
            openURL:(NSURL *)url
            options:(NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options {
  // 네이버 로그인 처리
  if ([url.scheme isEqualToString:@"helperit"]) {
    return [[NaverThirdPartyLoginConnection getSharedInstance]
              application:application
                    openURL:url
                    options:options];
  }

  // 카카오 로그인 처리
  if ([RNKakaoLogins isKakaoTalkLoginUrl:url]) {
    return [RNKakaoLogins handleOpenUrl:url];
  }

  // 기본 LinkingManager 처리
  return [RCTLinkingManager application:application openURL:url options:options];
}
```

## 적용 방법

1. Xcode에서 프로젝트 내 `AppDelegate.mm` 파일을 엽니다.
2. 상단에 네이버 및 카카오 로그인 관련 헤더 파일을 추가합니다:

```objc
 #import <NaverThirdPartyLogin/NaverThirdPartyLoginConnection.h>
 #import <RNKakaoLogins.h>
```

3. `- (BOOL)concurrentRootEnabled` 메서드를 구현하여 `true`를 반환하도록 설정합니다.
4. `application:openURL:options:` 메서드를 아래와 같이 수정하거나 추가합니다.
5. 수정 후, 프로젝트를 Clean & Build 하여 변경 사항이 반영되었는지 확인합니다.

이제 iOS에서 네이버 및 카카오 로그인이 정상 동작해야 합니다.
