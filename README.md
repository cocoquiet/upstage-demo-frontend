# 모닥 장부 프론트엔드

React와 Vite로 만든 영수증 장부 화면입니다. 브라우저에서 Upstage API 키를 사용하지 않고, 백엔드를 통해 영수증 분석과 장부 CRUD를 호출합니다.

## 로컬 실행

1. 백엔드를 `http://127.0.0.1:8000`에서 실행합니다.
2. 이 폴더에서 환경 파일을 만들고 프론트를 실행합니다.

```sh
cp .env.example .env
npm install
npm run dev
```

Vite 개발 서버는 `/api` 요청을 백엔드로 전달합니다. 백엔드 주소가 다르면 `.env`의 `VITE_API_PROXY_TARGET` 값을 변경하세요.

## 연결 API

- `GET /receipts`: 장부 목록을 불러옵니다.
- `POST /receipts/analyze`: multipart의 `file` 필드로 사진을 보내고 AI 분석 JSON을 받습니다.
- `POST /receipts`: 확인한 분석 초안을 장부에 저장합니다.
- `PATCH /receipts/{receipt_id}`: 검토 항목을 승인합니다.

분석 결과는 저장 전에 화면에서 수정할 수 있습니다. 배포 환경에서 백엔드에 직접 연결할 때는 `VITE_API_BASE_URL`을 백엔드 URL로 지정하고, 백엔드 CORS에서 프론트엔드 origin을 허용해야 합니다.
