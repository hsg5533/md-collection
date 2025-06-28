# React Native Android `ScreenStackFragment` 복원 오류 해결

Android에서 React Native 앱 실행 시 다음과 같은 오류가 발생할 수 있습니다:

```bash
Exception java.lang.RuntimeException: Unable to start activity ComponentInfo{kr.co.helperits.android/kr.co.helperits.android.MainActivity}: androidx.fragment.app.Fragment$InstantiationException: Unable to instantiate fragment com.swmansion.rnscreens.ScreenStackFragment: calling Fragment constructor caused an exception
  at android.app.ActivityThread.performLaunchActivity (ActivityThread.java:4184)
  at android.app.ActivityThread.handleLaunchActivity (ActivityThread.java:4340)
  at android.app.servertransaction.LaunchActivityItem.execute (LaunchActivityItem.java:101)
  at android.app.servertransaction.TransactionExecutor.executeCallbacks (TransactionExecutor.java:135)
  at android.app.servertransaction.TransactionExecutor.execute (TransactionExecutor.java:95)
  at android.app.ActivityThread$H.handleMessage (ActivityThread.java:2584)
  at android.os.Handler.dispatchMessage (Handler.java:106)
  at android.os.Looper.loopOnce (Looper.java:226)
  at android.os.Looper.loop (Looper.java:313)
  at android.app.ActivityThread.main (ActivityThread.java:8810)
  at java.lang.reflect.Method.invoke
  at com.android.internal.os.RuntimeInit$MethodAndArgsCaller.run (RuntimeInit.java:604)
  at com.android.internal.os.ZygoteInit.main (ZygoteInit.java:1067)
Caused by androidx.fragment.app.Fragment$InstantiationException: Unable to instantiate fragment com.swmansion.rnscreens.ScreenStackFragment: calling Fragment constructor caused an exception
  at androidx.fragment.app.Fragment.instantiate (Fragment.java:631)
  at androidx.fragment.app.FragmentContainer.instantiate (FragmentContainer.java:57)
  at androidx.fragment.app.FragmentManager$3.instantiate (FragmentManager.java:483)
  at androidx.fragment.app.FragmentStateManager.<init> (FragmentStateManager.java:85)
  at androidx.fragment.app.FragmentManager.restoreSaveState (FragmentManager.java:2728)
  at androidx.fragment.app.FragmentController.restoreSaveState (FragmentController.java:198)
  at androidx.fragment.app.FragmentActivity$2.onContextAvailable (FragmentActivity.java:149)
  at androidx.activity.contextaware.ContextAwareHelper.dispatchOnContextAvailable (ContextAwareHelper.java:99)
  at androidx.activity.ComponentActivity.onCreate (ComponentActivity.java:322)
  at androidx.fragment.app.FragmentActivity.onCreate (FragmentActivity.java:273)
  at com.facebook.react.ReactActivity.onCreate (ReactActivity.java:45)
  at android.app.Activity.performCreate (Activity.java:8657)
  at android.app.Activity.performCreate (Activity.java:8636)
  at android.app.Instrumentation.callActivityOnCreate (Instrumentation.java:1417)
  at android.app.ActivityThread.performLaunchActivity (ActivityThread.java:4165)
Caused by java.lang.reflect.InvocationTargetException:
  at java.lang.reflect.Constructor.newInstance0
  at java.lang.reflect.Constructor.newInstance (Constructor.java:343)
  at androidx.fragment.app.Fragment.instantiate (Fragment.java:613)
Caused by java.lang.IllegalStateException: Screen fragments should never be restored. Follow instructions from https://github.com/software-mansion/react-native-screens/issues/17#issuecomment-<US_SOCIAL_SECURITY_NUMBER> to properly configure your main activity.
  at com.swmansion.rnscreens.ScreenFragment.<init> (ScreenFragment.kt:54)
  at com.swmansion.rnscreens.ScreenStackFragment.<init> (ScreenStackFragment.kt:35)
```

## 1. 원인

- Android는 Activity 재시작 과정 중에 뷰(View) 상태를 자동 복원하려고 시도합니다.
- React Native Screens 라이브러리의 `ScreenFragment`는 복원을 지원하지 않아, Activity 재시작 시 복원된 상태로 인해 예외가 발생합니다.

## 2. 해결 방법

`MainActivity.java` 파일에서 `onCreate` 메서드를 오버라이드하여 전달된 `Bundle`을 **null**로 넘겨주면, 액티비티가 상태 복원을 시도하지 않습니다.

1. **파일 위치**

```bash
android/app/src/main/java/<당신의_패키지_이름>/MainActivity.java
```

2. **수정할 코드**

```java
import android.os.Bundle;
import com.facebook.react.ReactActivity;
import com.facebook.react.ReactActivityDelegate;

public class MainActivity extends ReactActivity {

    // 기존 코드...

    // react-native-screens 충돌 방지를 위한 오버라이드
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(null);
    }

    public static class MainActivityDelegate extends ReactActivityDelegate {
        // 기존 코드...
    }
}
```

3. **적용 후**
   - 프로젝트를 Clean & Rebuild 합니다:

```bash
cd android
./gradlew clean
cd ..
npx react-native run-android
```

- 화면 복원 오류가 제거되어 앱이 정상 실행됩니다.
