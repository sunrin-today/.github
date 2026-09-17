![Cover Image](https://raw.githubusercontent.com/sunrin-today/.github/assets/banner_rounded.png)

# Sunrin Today

선린인터넷고등학교 급식 서비스 · [@sunrin_today](https://instagram.com/sunrin_today)

- [api](https://github.com/sunrin-today/api) — 급식 조회/쓰기
- [meal-uploader](https://github.com/sunrin-today/meal-uploader) — 나이스 → API
- [instagram-uploader](https://github.com/sunrin-today/instagram-uploader) — API → Instagram

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

### Administrator

- [Jeewon Kwon](https://github.com/jwkwon0817)
- [Sungju Cho](https://github.com/iamfiro)
