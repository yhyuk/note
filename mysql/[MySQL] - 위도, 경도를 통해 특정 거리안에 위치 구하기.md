# [MySQL] - 위도, 경도를 통해 특정 거리안에 위치 구하기

구글 지도를 열고 한 지점을 선택하면 해당 위치의 '위도'와 '경도'가 나온다. 이처럼 기준 위도, 경도와 특정 위치의 위도, 경도를 가지고 기준점에서의 거리를 mysql을 통해 구할 수 있다.

### 현재위치

- 위도 : mylat
- 경도 : mylng

### 지정 위치

- 위도 : pointlat
- 경도 : pointlng

```sql
SELECT
		(6371*acos(cos(radians(mylat))*cos(radians(pointlat))*cos(radians(pointlng)
    -radians(mylng))+sin(radians(mylat))*sin(radians(pointlat)))) AS distance
FROM 테이블
HAVING distance <= 거리
ORDER BY distance ASC
```

→ **현재 위치**에 근접한 **지정 위치**를 가까운 순서대로 가져오는 쿼리이다.

→ 현재 위/경도를 통해 mysql에서 많이 사용하는 일종의 공식이다