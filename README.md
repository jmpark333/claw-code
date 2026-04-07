# Claw Code - Ollama/OpenAI 호환 API 버전

Claw Code의 Ollama 및 OpenAI 호환 API 지원 버전입니다.

## 설치

```bash
cd rust
cargo build --release
cargo install --path .
```

## API 설정

`~/.claw/config.json` 파일 생성:

**Ollama (로컬 LLM - API 키 불필요):**

```json
{
  "provider": "openai-compatible",
  "api_key": "",
  "base_url": "http://localhost:11434/v1",
  "model": "qwen2.5:7b"
}
```

**OpenAI 호환 API (Z.AI, OpenRouter 등):**

```json
{
  "provider": "openai-compatible",
  "api_key": "your-api-key",
  "base_url": "https://api.z.ai/api/coding/paas/v4",
  "model": "glm-5"
}
```

## 사용법

```bash
# 대화형 모드
claw

# 단발성 프롬프트
claw prompt "이 저장소를 요약해줘"

# 모델 지정
claw --model qwen2.5:7b "파이썬 코드 작성해줘"
```

## 지원 모델

- **Ollama**: qwen, llama, gemma, mistral, exaone, granite
- **클라우드**: Z.AI, OpenRouter, NVIDIA NIM

## Ollama 설치

```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull qwen2.5:7b
```

## 추가된 기능

- OpenAI 호환 API 지원 (Ollama, Z.AI 등)
- config.json으로 API 설정
- API 키 없이 Ollama 사용 가능

## 참고

- 원본: https://github.com/ultraworkers/claw-code
- 이 fork: https://github.com/jmpark333/claw-code

## 라이선스

MIT License