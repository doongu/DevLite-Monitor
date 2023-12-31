## 1. nodes
otel_traces 테이블에서 각 서비스별로 평균 지속 시간, 요청 수, 오류 비율 등의 통계를 계산하여 반환합니다.
- 밀리세컨드를 세컨드로 변환을 위해 Duration 컬럼의 평균값을 계산하고, 그 결과를 1000으로 나누어 mainstat이라는 이름으로 가져옵니다.
- 전체 로우의 개수를 계산하고, 그 결과를 문자열로 변환한 후 "req cnt "라는 문자열과 연결(concatenate)하여 secondarystat라는 이름으로 가져옵니다.
- StatusCode 값이 'STATUS_CODE_ERROR'인 로우의 비율을 계산합니다. 이 값을 백분율로 변환하고 문자열로 바꾼 후 '%'를 추가하여 detail__ERROR_RATE라는 이름으로 가져옵니다.
- 결과를 ServiceName 값별로 그룹화하여, 각 서비스별로 평균 지속 시간, 요청 수, 오류 비율 등의 통계를 계산하여 반환합니다.

## 1-2. edges
otel_traces 테이블에서 두 서비스 간의 상호 작용(예: 서비스 A에서 서비스 B로의 요청)과 그에 관한 통계(응답 시간, 요청 횟수, 오류 비율)를 추출합니다.

●	 서비스 간 호출의 평균 응답 시간을 나타내기 위해 t.Duration의 평균값을 계산하고, 그 결과를 1000으로 나누어 **`detail__RESPONSE_TIME이라는 이름으로 가져옵니다.

●	두 서비스 간의 총 요청 횟수를 나타내기 위해 전체 로우의 개수를 계산하고, 그 결과를 문자열로 변환하여 detail__REQUEST_COUNT라는 이름으로 가져옵니다.

●	t.StatusCode 값이 'ERROR'인 로우의 비율을 계산합니다. 이 값을 백분율로 변환하고 문자열로 바꾼 후 '%'를 추가하여 detail__ERROR_RATE라는 이름으로 가져옵니다.
