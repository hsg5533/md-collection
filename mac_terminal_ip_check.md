# Mac에서 터미널을 이용한 IP 주소 확인

## 우선적으로 사용되는 네트워크 IP 확인

```bash
ipconfig getifaddr en0
```

## 전체 네트워크 확인

```bash
ifconfig
```

## 복수의 네트워크에 연결되어 있을 때 IP 확인

```bash
ifconfig | grep inet
```
