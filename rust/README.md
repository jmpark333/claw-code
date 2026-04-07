# Claw Code - Ollama/OpenAI 호환 API 버전

Claw Code의 Ollama 및 OpenAI 호환 API 지원 버전입니다. 로컬 LLM(Ollama)과 다양한 OpenAI 호환 API 제공자를 사용할 수 있습니다.

## 설치

### 사전 요구사항

- Rust stable toolchain
- Cargo
- Ollama (로컬 LLM 사용 시)

### 빌드

```bash
cd rust
cargo build --release
```

### 설치

```bash
cargo install --path .
```

## API 설정

### 방법 1: config.json 파일 (권장)

`~/.claw/config.json` 파일을 생성합니다:

**Ollama (로컬 LLM - API 키 불필요):**

```json
{
  "provider": "openai-compatible",
  "api_key": "",
  "base_url": "http://localhost:11434/v1",
  "model": "qwen2.5:7b"
}
```

**OpenAI 호환 API (Z.AI, OpenRouter, NVIDIA NIM 등):**

```json
{
  "provider": "openai-compatible",
  "api_key": "your-api-key",
  "base_url": "https://api.z.ai/api/coding/paas/v4",
  "model": "glm-5"
}
```

### 방법 2: 환경 변수

```bash
export ANTHROPIC_API_KEY="sk-ant-..."
export XAI_API_KEY="xai-..."
```

## 지원 모델

### Ollama 로컬 모델
- `qwen` 시리즈 (qwen2.5:7b, qwen3.5:2b 등)
- `llama` 시리즈 (llama3.2 등)
- `gemma` 시리즈
- `mistral` 시리즈
- `exaone` 시리즈
- `granite` 시리즈

### 클라우드 API
- Z.AI (glm-5, glm-4.7-flash)
- OpenRouter
- NVIDIA NIM API
- 기타 OpenAI 호환 API

## 사용법

### 대화형 모드

```bash
claw
```

### 단발성 프롬프트

```bash
claw prompt "이 저장소를 요약해줘"
```

### 모델 지정

```bash
claw --model qwen2.5:7b "파이썬 코드 작성해줘"
claw -m glm-5 "코드 리뷰해줘"
```

### 슬래시 명령어

| 명령어 | 설명 |
|--------|------|
| `/help` | 도움말 표시 |
| `/status` | 현재 상태 확인 |
| `/compact` | 대화 기록 압축 |
| `/config` | 설정 확인 |

## Ollama 설정

### Ollama 설치

```bash
# macOS/Linux
curl -fsSL https://ollama.com/install.sh | sh

# 모델 다운로드
ollama pull qwen2.5:7b
ollama pull llama3.2
```

### Ollama 실행 확인

```bash
ollama list
ollama run qwen2.5:7b
```

## 구현 내용

이 버전에서 추가된 기능:

1. **OpenAI 호환 API 지원** - Ollama, Z.AI, OpenRouter 등 연동
2. **config.json 설정** - 환경 변수 없이 파일로 API 설정
3. **Bearer 인증 선택적 적용** - Ollama처럼 API 키가 필요 없는 provider 지원
4. **다양한 로컬 모델 지원** - exaone, llama, gemma, mistral, granite 등

## 제한사항

- Windows 지원이 미흡할 수 있음
- 일부 모델은 function calling(도구 사용)을 지원하지 않음
- 초기 버전(0.1.0)으로 API가 변경될 수 있음

## 참고

- 원본 저장소: https://github.com/ultraworkers/claw-code
- 이 fork: https://github.com/jmpark333/claw-code

## 라이선스

MIT License