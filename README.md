# 📱 Apache Cordova를 활용한 앱 개발 수업

## 🧾 수업 개요

Apache Cordova는 HTML, CSS, JavaScript와 같은 웹 기술을 사용하여 **하이브리드 모바일 애플리케이션**을 개발할 수 있는 오픈 소스 프레임워크입니다. 이 수업에서는 Cordova를 사용하여 **안드로이드 및 iOS 앱**을 개발하는 방법을 실습을 통해 익힙니다.

---

## 🛠️ 준비 사항

### 필수 소프트웨어
- Node.js (https://nodejs.org/)
- npm (Node 패키지 관리자)
- Git (https://git-scm.com/)
- Cordova CLI
- Android Studio (Android 개발용)
- Xcode (iOS 개발용, macOS에서만)

### Cordova CLI 설치
```bash
npm install -g cordova
```

---

## 🗂️ 프로젝트 구조

Cordova 프로젝트는 다음과 같은 디렉토리 구조를 가집니다:

```
myApp/
├── config.xml
├── hooks/
├── platforms/
├── plugins/
├── www/
└── package.json
```

- `www/`: 실제 앱의 소스 (HTML, CSS, JS)
- `platforms/`: Android 또는 iOS와 같은 플랫폼별 코드
- `plugins/`: 네이티브 기능을 추가하는 Cordova 플러그인

---

## ⚙️ 앱 개발 절차

1. **Cordova 프로젝트 생성**
   ```bash
   cordova create myApp com.example.myapp MyApp
   cd myApp
   ```

2. **플랫폼 추가**
   ```bash
   cordova platform add android
   # 또는
   cordova platform add ios
   ```

3. **앱 코드 작성 (`www/index.html` 등)**

4. **플러그인 추가 (예: 카메라)**
   ```bash
   cordova plugin add cordova-plugin-camera
   ```

5. **앱 빌드**
   ```bash
   cordova build android
   # 또는
   cordova build ios
   ```

6. **앱 실행 (에뮬레이터 또는 실제 디바이스)**
   ```bash
   cordova run android
   ```

---

## 👨‍💻 실습 예제: 간단한 카메라 앱

### 📌 목표
- 사용자로부터 사진을 찍고 결과를 화면에 표시

### 주요 코드 (`www/js/index.js`)
```javascript
document.getElementById("takePictureBtn").addEventListener("click", () => {
  navigator.camera.getPicture(
    (imageData) => {
      document.getElementById("photo").src = "data:image/jpeg;base64," + imageData;
    },
    (error) => {
      alert("Camera failed: " + error);
    },
    {
      quality: 50,
      destinationType: Camera.DestinationType.DATA_URL
    }
  );
});
```

### HTML (`www/index.html`)
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>카메라 앱</title>
  </head>
  <body>
    <button id="takePictureBtn">사진 찍기</button>
    <img id="photo" src="" />
    <script src="js/index.js"></script>
  </body>
</html>
```

---

## 🧩 자주 사용하는 Cordova 플러그인

| 플러그인 이름               | 설명                  |
|----------------------------|-----------------------|
| cordova-plugin-camera      | 카메라 접근           |
| cordova-plugin-geolocation | 위치 정보 접근        |
| cordova-plugin-device      | 디바이스 정보 확인    |
| cordova-plugin-dialogs     | 네이티브 알림/확인창 |
| cordova-plugin-network-information | 네트워크 상태 확인 |

---

## 📚 참고 자료

- [Cordova 공식 문서](https://cordova.apache.org/docs/)
- [플러그인 검색](https://cordova.apache.org/plugins/)
- [MDN Web Docs](https://developer.mozilla.org/)

---
