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
