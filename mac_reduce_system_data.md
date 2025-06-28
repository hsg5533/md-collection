# Mac 시스템 데이터 줄이기

Mac의 시스템 데이터 사용량을 줄이기 위해 다음 명령어를 실행합니다. **실행 전 중요한 데이터가 삭제되지 않도록 주의하세요.**

1. **맥 내부 캐시 삭제**

```bash
rm -rf ~/Library/Caches
```

2. **앱 전용 데이터 삭제**
   > 삭제 시 해당 앱의 설정 및 데이터가 초기화될 수 있습니다.

```bash
rm -rf ~/Library/Containers
```

3. **Application Scripts 삭제**

```bash
rm -rf ~/Library/Application\ Scripts
```

4. **Application Support 삭제**

```bash
rm -rf ~/Library/Application\ Support
```

이 명령어들은 시스템 데이터를 삭제하여 저장 공간을 확보하는 데 도움이 됩니다. 사용 후 시스템 재시작을 권장합니다.
