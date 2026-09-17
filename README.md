![Cover Image](https://raw.githubusercontent.com/sunrin-today/.github/assets/banner_rounded.png)

# 선린투데이

선린인터넷고등학교 급식 서비스입니다.

- [api](https://github.com/sunrin-today/api) — 급식 조회/쓰기
- [meal-uploader](https://github.com/sunrin-today/meal-uploader) — NEIS → API
- [instagram-uploader](https://github.com/sunrin-today/instagram-uploader) — API → Instagram [@sunrin_today](https://instagram.com/sunrin_today)

## 아키텍처

```mermaid
flowchart LR
  Scheduler[Cloud Scheduler] --> MealJob[meal-uploader Job]
  Scheduler --> IgJob[instagram-uploader Job]
  MealJob --> Neis[NEIS OpenAPI]
  MealJob --> API[api.sunrin.kr]
  IgJob --> API
  IgJob --> GCS[GCS]
  GCS --> Graph[Instagram Graph API]
  IgJob --> Graph
  MealJob --> Discord[Discord]
  IgJob --> Discord
  API --> PG[(PostgreSQL)]
  API --> Redis[(Redis)]
  SM[Secret Manager] --> MealJob
  SM --> IgJob
  SM --> API
```
