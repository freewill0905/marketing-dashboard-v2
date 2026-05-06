# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI 마케팅 팀 대시보드(MKTG-OS v2.6). `index.html`은 Anthropic API를 백엔드로 사용하는 싱글 페이지 마케팅 AI 대시보드다. `api/chat.js`는 Vercel Serverless Function으로 ANTHROPIC_API_KEY를 서버 사이드에서 처리한다.

## Stack

- **Frontend**: Vanilla JS + HTML/CSS (빌드 없음, 번들러 없음)
- **Backend**: Vercel Serverless Function (`api/chat.js`) — Anthropic API 프록시
- **Deploy**: Vercel (`vercel.json` 참고)
- **AI Skills**: `ai-marketing-claude/` — 별도 git 저장소, Claude Code 마케팅 스킬 모음

## Local Dev

```bash
# Vercel CLI로 로컬 실행 (api/ 함수 포함)
npx vercel dev

# 또는 정적 파일만 확인할 때
npx serve .
```

환경 변수: `ANTHROPIC_API_KEY`는 Vercel 대시보드에서 설정. 로컬에서는 `.env.local`에 작성.

## Key Files

- `index.html` — 메인 대시보드 (모든 UI + Claude API 호출 로직 포함)
- `api/chat.js` — Anthropic API 프록시 (CORS 처리 포함)
- `vercel.json` — 배포 설정
- `ai-marketing-claude/` — 마케팅 분석 스킬 모음 (독립 저장소, 직접 편집 불필요)

## AI Agents & Commands

이 프로젝트에는 마케터용 Claude Code 에이전트와 커스텀 명령어가 포함되어 있다:

| 에이전트 | 용도 |
|---|---|
| `content-writer` | 블로그·SNS·광고 카피 초안 작성 |
| `campaign-analyst` | 캠페인 성과 분석 및 개선안 도출 |
| `seo-specialist` | 키워드 리서치 및 SEO 최적화 |

| 명령어 | 용도 |
|---|---|
| `/copy <product>` | 광고 카피 5종 즉시 생성 |
| `/post <topic>` | SNS 플랫폼별 포스팅 생성 |
| `/brief <campaign>` | 마케팅 브리프 문서 작성 |
| `/weekly-report` | 주간 마케팅 성과 보고서 |
| `/translate <lang>` | 마케팅 콘텐츠 현지화 번역 |

## 기본 규칙
- 불확실한 정보는 "모릅니다" 또는 "확실하지 않습니다"라고 명확히 말할 것
- 사실과 데이터를 기반으로만 답변할 것, 추측 금지
- 마케팅 답변은 항상 실행 가능한 액션 아이템 포함
- 수치와 데이터 제시 시 출처 명확히 할 것
- 경쟁사 분석 시 근거 없는 비방 금지

## 식품/건강기능식품 광고심의 준수 규칙
(근거: 식품 등의 표시·광고에 관한 법률 제8조, 식품의약품안전처 기준)

### 절대 금지 표현
- 질병 예방·치료 효능 표현 금지
  예) "당뇨 치료", "고혈압 예방", "암 예방", "간염 개선", "체질 개선"
- 의약품으로 오인할 수 있는 표현 금지
  예) "복용", "즉각적인 치료 효과", "특효"
- 거짓·과장 표현 금지
  예) "100% 효과", "완벽한 효능", "특효"
- 근거 없는 타사 비교 표현 금지
- 소비자 기만 표현 금지

### 올바른 표현 방법
- "~에 도움을 줄 수 있음" (식약처 인정 기능성 범위 내에서만)
- 수치 비교 시 반드시 출처 명시
- 건강기능식품은 반드시 "건강기능식품" 표시 포함

### 콘텐츠 생성 시 주의사항
- 위 금지 표현이 포함된 카피 생성 요청 시 반드시 수정하여 제안
- 광고심의에 걸릴 수 있는 표현 발견 시 대체 표현 함께 제시
