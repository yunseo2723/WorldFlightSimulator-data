# WorldFlightSimulator 자료 저장소

게임 파일(Roblox Place 100 MB 제한)에 넣기에는 큰 자료입니다. 게임 서버가 필요할 때 HTTP로 받습니다 (`ServerStorage.DataHost`).

| 폴더 | 내용 | 만드는 도구 |
|---|---|---|
| `airports/<ICAO>.json` | 공항 상세 (활주로, 유도로, 건물, 주기장, 탑승교 ...) | `tools/osm_airport.py` |
| `heightfields/<섹터>/Chunk_XX.txt` | 지형 높이맵 (압축 d1, base64) | `tools/terrain/build_glb.py` (Blender) |
| `worldtiles/` | 전 세계 상세 지형 1/24° (세계지도) | `tools/world/build_world_data.py` |

## 올리는 방법 (처음 한 번)

1. GitHub에서 **공개(Public)** 저장소를 만듭니다 (예: `WorldFlightSimulator-data`).
2. 이 `cdn` 폴더에서:
   ```bash
   git init -b main
   git add .
   git commit -m "자료"
   git remote add origin https://github.com/<아이디>/WorldFlightSimulator-data.git
   git push -u origin main
   ```
3. `src/serverstorage/DataHost.luau` 맨 위 `GITHUB` 에 아이디와 저장소 이름을 적습니다.
4. Roblox Studio: 게임 설정 → 보안 → **Allow HTTP Requests** 켜기.

자료를 다시 만들면 이 폴더에서 `git add . && git commit && git push` 만 하면 됩니다.
(jsDelivr 캐시 때문에 반영까지 최대 12시간 걸릴 수 있습니다. 그동안은 GitHub raw 로도 받습니다.)

데이터 출처: © OpenStreetMap contributors (ODbL), Copernicus DEM, ESA WorldCover 2021 (CC BY 4.0)
