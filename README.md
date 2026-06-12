# 과정설문 분석기 — Vercel 배포 가이드

## 폴더 구조
```
.
├── index.html       # 메인 앱
├── api/
│   └── analyze.js   # Claude API 프록시 (서버리스 함수)
└── vercel.json
```

## 배포 절차

### 1. GitHub에 업로드
이 폴더 전체를 새 GitHub 저장소에 푸시합니다.

```bash
git init
git add .
git commit -m "초기 배포"
git branch -M main
git remote add origin <레포 URL>
git push -u origin main
```

### 2. Vercel에 연결
1. https://vercel.com → New Project → 위 GitHub 저장소 선택
2. Framework Preset: **Other** (자동 감지됨)
3. 배포 전 **Environment Variables** 추가:
   - Key: `ANTHROPIC_API_KEY`
   - Value: (발급받은 Claude API 키, `sk-ant-...`)
   - Environment: Production, Preview, Development 모두 체크
4. **Deploy** 클릭

### 3. 확인
배포 완료 후 발급된 URL(예: `https://your-app.vercel.app`)로 접속하여
- 엑셀 업로드 → 보고서 표시
- "AI 인사이트 분석 시작" 클릭 → 정상 동작 확인

## 주의사항
- API 키는 절대 `index.html`이나 GitHub에 직접 입력하지 마세요. (Vercel 환경변수로만 관리)
- 환경변수 변경 후에는 **Redeploy**가 필요합니다.
- PDF 다운로드는 브라우저 인쇄(Ctrl+P) → "PDF로 저장"을 이용합니다.
