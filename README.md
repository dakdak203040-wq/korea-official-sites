# korea-official-sites — 한국 공식 사이트 주소 데이터

포털, 은행, 정부·공공기관, OTT, 쇼핑 등 한국에서 자주 쓰는 서비스의 **검증된 공식 홈페이지 주소** 목록입니다.
데이터는 [주소핀](https://jusopin.com)에서 사람이 공식 출처로 확인하고, 30분마다 자동 접속 점검을 거친 사이트만 담습니다.
매일 자동으로 갱신됩니다.

## 파일

| 파일 | 설명 |
|---|---|
| `sites.json` | 전체 목록 (JSON). `name`, `url`, `category`, `categoryName`, `operator`, `operatorType`, `verifiedAt`, `page` |
| `sites.csv` | 같은 내용의 CSV (엑셀에서 바로 열림) |

원본: https://jusopin.com/data/sites.json

## 쓰임새

- 피싱·스미싱 탐지: 사용자가 받은 링크의 도메인이 공식 도메인과 다른지 비교
- 브라우저 확장, 챗봇, 사내 포털의 "공식 사이트 바로가기"
- 도메인 변경 추적 연구 (주소핀은 도메인 변경을 감지해 반영합니다)

```js
const res = await fetch("https://raw.githubusercontent.com/dakdak203040-wq/korea-official-sites/main/sites.json");
const { sites } = await res.json();
const official = new Set(sites.map(s => new URL(s.url).hostname.replace(/^www\./, "")));
```

## 등록 기준

- 합법적으로 운영되는 서비스의 공식 홈페이지만 등록합니다. 도박·성인·불법 공유·차단 우회 사이트는 넣지 않습니다.
- 각 주소는 운영 주체의 공식 발표, 앱스토어 개발자 정보 등 두 곳 이상의 출처로 확인합니다.
- 자세한 기준: https://jusopin.com/criteria

## 기여

빠진 사이트나 바뀐 주소는 이 저장소에 이슈를 남기거나 https://jusopin.com/report 로 알려 주세요.
공식 발표 링크를 함께 주시면 빨리 반영됩니다.

## 라이선스

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ko) — 자유롭게 쓰되 출처(주소핀, https://jusopin.com)를 표시해 주세요.
