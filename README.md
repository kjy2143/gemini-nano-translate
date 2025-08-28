# Gemini Nano Translate

크롬 브라우저에 내장된 AI API를 활용하여 웹 페이지의 언어를 감지하고 번역하는 크롬 확장프로그램입니다.

## 주요 기능

- **언어 자동 감지**: Language Detector API를 활용하여 원본 문서의 언어를 자동으로 감지
- **양방향 번역**: Translator API를 활용하여 다양한 언어 간 번역 지원
- **몰입형 번역**: 원문과 번역문을 문단 단위로 이중언어 표시 (원문 바로 아래에 번역문 삽입)
- **스마트 언어 선택**: 출발어는 자동 감지, 도착어는 사용자 브라우저 언어 기반 기본값 설정

## 전제 조건

크롬 AI API를 사용하기 위해 다음 설정이 필요합니다:

### 1. 크롬 버전
- Chrome 138 이상 설치

### 2. 플래그 활성화
다음 URL에서 해당 플래그들을 활성화하세요:

```
chrome://flags/#optimization-guide-on-device-model
```
- **Enabled BypassPrefRequirement** 활성화

```
chrome://flags/#prompt-api-for-gemini-nano
```
- **Enabled** 활성화

### 3. 컴포넌트 업데이트
```
chrome://components/
```
- **Optimization Guide On Device Model** 항목에서 **Check for update** 버튼 클릭

## 사용된 API

### Language Detector API
- **용도**: 웹 페이지 원본 언어 자동 감지
- **참고 문서**: [Chrome Language Detection API](https://developer.chrome.com/docs/ai/language-detection?hl=ko)

### Translator API
- **용도**: 텍스트 번역 처리
- **참고 문서**: [Chrome Translator API](https://developer.chrome.com/docs/ai/translator-api?hl=ko)

## 지원 언어

양방향 번역이 지원되는 LLM 지원 언어는 [Google Cloud Translation API 언어 목록](https://cloud.google.com/translate/docs/languages?hl=ko#adaptive_translation)을 참고하세요.

## 번역 방식

### 몰입형 번역 (Immersive Translation)
원문 문단 내에 번역문을 삽입하는 방식으로 구현됩니다:

```html
<p>
  원문 내용...
  <font class="gemini-nano-translate-target-wrapper" lang="ko">
    번역된 내용...
  </font>
</p>
```

### 언어 선택 로직
- **출발어 (Source Language)**: Language Detector API로 자동 감지된 언어를 기본값으로 설정
- **도착어 (Target Language)**: `navigator.language`를 기반으로 사용자 브라우저 언어를 기본값으로 설정
- **사용자 선택**: 셀렉트 박스를 통해 원하는 언어로 변경 가능

## 설치 및 사용

1. 전제 조건에 명시된 크롬 설정 완료
2. 확장프로그램 설치
3. 번역하고 싶은 웹 페이지에서 확장프로그램 실행
4. 언어 자동 감지 및 번역 시작

## 개발 환경

- **빌드 도구**: CRXJS (Chrome Extension Vite Plugin)
- **개발 언어**: TypeScript (Vanilla, 별도 프레임워크 없음)
- **번들러**: Vite

## 기술 스택

- Chrome Extension API (Manifest V3)
- Chrome Built-in AI APIs
  - Language Detector API
  - Translator API
- TypeScript/HTML/CSS
- CRXJS (Chrome Extension 개발 도구)

## 참고 자료

- [Chrome Built-in AI APIs](https://developer.chrome.com/docs/ai/built-in-apis?hl=ko)
- [Language Detection API](https://developer.chrome.com/docs/ai/language-detection?hl=ko)
- [Translator API](https://developer.chrome.com/docs/ai/translator-api?hl=ko)
- [Google Cloud Translation Languages](https://cloud.google.com/translate/docs/languages?hl=ko#adaptive_translation)

## 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다.
