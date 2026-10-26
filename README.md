# 📚 인천외고 영어 내신 분석 에이전트

모의고사 지문을 **외고 내신 1등급 수준**으로 14단계 심층 분석하고,
변형 문제 24개 + 킬러 문제 3개 + 암기 노트까지 만들어 주는 Claude Code 에이전트입니다.

- 현재 범위: **2026학년도 10월 고1 전국연합학력평가 영어 18~45번** (`config.md`에서 변경)

---

## 📁 구성

```
incheon-fl-english-agent/
├── README.md
├── config.md                        ← 시험 범위 설정 (시험 바뀌면 여기만 수정)
├── .gitignore                       ← 지문·결과물·PDF 업로드 차단
├── .claude/
│   └── agents/
│       └── naesin-analyzer.md       ← 에이전트 본체 (역할 + 14단계 + 지시사항)
├── templates/
│   ├── output-format.md             ← 문항별 14단계 출력 양식
│   └── cumulative-test.md           ← 누적 암기 테스트 20문제 양식
├── prompts/
│   └── standalone-prompt.md         ← 채팅창에 붙여넣는 버전
├── passages/                        ← 지문 넣는 곳 (git 제외)
│   └── README.md                    ← 파일 이름 규칙
└── output/                          ← 분석 결과 저장 (git 제외)
```

---

## 🚀 사용법

### 방법 A. Claude Code (에이전트로 사용)

1. 저장소 받기
   ```bash
   git clone https://github.com/<내아이디>/incheon-fl-english-agent.git
   cd incheon-fl-english-agent
   ```
2. `passages/` 폴더에 지문 넣기 → 규칙은 [`passages/README.md`](passages/README.md)
   - 예: `passages/18.txt`, `passages/41-42.txt`
3. Claude Code 실행 후 요청
   ```
   naesin-analyzer로 18번 분석해줘
   ```
   → 결과가 `output/18번.md`로 저장됩니다.
4. 범위를 다 끝낸 뒤
   ```
   naesin-analyzer로 누적 암기 테스트 만들어줘
   ```

> 💡 **한 번에 한 문항씩** 요청하세요. 14단계 × 여러 문항은 출력이 너무 길어 잘립니다.

### 방법 B. 채팅 (Claude 웹/앱, 기타 AI)

1. [`prompts/standalone-prompt.md`](prompts/standalone-prompt.md) 내용을 복사
2. Claude 프로젝트의 "지침(instructions)"에 붙여넣거나, 대화 첫 메시지로 붙여넣기
3. 지문 하나를 붙여넣고 "이 지문을 14단계로 분석해줘"

---

## 🧠 분석 14단계

| # | 단계 | # | 단계 |
|---|---|---|---|
| 1 | 지문 완전 해석 (직역+의역) | 8 | 배경지식 |
| 2 | 핵심 내용 요약 | 9 | 시험 출제 예상 문장 5개 |
| 3 | 주요 단어 15개+ | 10 | 서술형 대비 3문제 |
| 4 | 단어 심층 (동의어·반의어·파생어) | 11 | 영작 대비 3문제 |
| 5 | 숙어 정리 | 12 | 변형 문제 24개 (8유형×3) |
| 6 | 구문 분석 (트리 구조) | 13 | 상위 1% 킬러 문제 3개 |
| 7 | 어법 포인트 | 14 | 시험 전날 암기 노트 |

+ 문항마다 **출제 가능성 TOP 5**, 전 항목 **★1~★5 중요도**

---

## 🔄 다른 시험에 재사용하기

1. `config.md`의 시험 이름과 범위 수정
2. `passages/` 비우고 새 지문 넣기
3. 끝 — 에이전트 파일은 그대로 사용

---

## ⚠️ 저작권 안내

전국연합학력평가 문제지·해설지는 **무단 전재 및 재배포가 금지**되어 있습니다.

- 이 저장소에는 **프롬프트와 양식만** 포함되어 있으며, 지문은 포함되어 있지 않습니다.
- `.gitignore`가 `passages/`, `output/`, `*.pdf`를 자동으로 제외합니다.
- 분석 결과물에는 지문 해석이 들어 있으므로 **public 저장소에 올리지 마세요.**
  결과까지 보관하려면 저장소를 **Private**으로 만드세요.
