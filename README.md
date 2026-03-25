# 업무일지 — Claude Code 사용 가이드

## 파일 구조

```
work_diary/
├── index.html   ← 브라우저에서 열면 됩니다 (UI 렌더링)
├── data.js      ← 업무 내용은 여기서만 수정합니다
└── README.md
```

## 사용법

### 브라우저에서 열기
```bash
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

### Claude Code에서 수정 요청 예시
```
data.js 열어서 수요일 tasks에 "서류심사 평가기준표 완성" 추가해줘
```
```
역량강화교육 3회차 강사를 "김철수 대표"로, status를 "done"으로 바꿔줘
```
```
모집 현황 current를 17로 업데이트해줘
```
```
다음 주(3/30~4/5) 일정으로 새 주차 만들어줘
```

---

## data.js 수정 포인트

### 1. 오늘 알림 바 수정
```js
meta: {
  todayAlert: "🚨 새 알림 내용 여기에",
  recruitProgress: { current: 17, total: 20, deadline: "3월 29일 자정" }
}
```

### 2. 특정 날 할 일 추가/수정
```js
// days 배열에서 해당 id를 찾아 tasks에 추가
{
  priority: "urgent",   // urgent | warn | info | done
  category: "배지 텍스트",
  title: "할 일 제목",
  desc: "상세 설명"
}
```

### 3. 서포터즈 모집 현황 숫자 변경
```js
recruitProgress: { current: 17, total: 20, deadline: "3월 29일 자정" }
```

### 4. 역량강화교육 강사 확정
```js
{ instructor: "강사 이름", status: "done" }
```

### 5. 새 주차로 교체
`days` 배열 전체를 새 날짜로 교체하고,
`meta.weekLabel`, `meta.weekRange` 수정

---

## priority 색상 의미

| priority | 색상 | 사용 기준 |
|----------|------|-----------|
| urgent   | 빨강 | 오늘 반드시 처리 |
| warn     | 주황 | 이번 주 처리 필요 |
| info     | 파랑 | 준비·진행 중 |
| done     | 초록 | 완료됨 |
