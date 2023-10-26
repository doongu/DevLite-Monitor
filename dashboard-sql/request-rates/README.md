## Request Rates
otel_traces 테이블에서 각 서비스의 특정 시간에 대한 요청 비율을 계산하고 그 결과를 시간별로 정렬하여 반환하는 것입니다.

●	첫 번째 공통 테이블 표현식(CTE)인 RequestCounts를 정의합니다.

●	각 로우의 Timestamp을 해당 분의 시작 시간으로 변경하고, 서비스 이름과 해당 시간과 서비스의 조합별로 로우의 수(요청 수)를 계산합니다.

●	toStartOfMinute(Timestamp): 각 로우의 Timestamp를 해당하는 분의 시작 시간으로 바꿉니다. 이렇게 하면 시간을 분 단위로 그룹화 할 수 있습니다.

●	Grafana의 매크로를 사용하여 조건을 지정합니다. 여기서는 3가지 조건이 있습니다:
1.	Grafana의 매크로 $__conditionalAll를 사용하여, TraceId가 주어진 변수 trace_id 값들 중 하나와 일치하는지 결정합니다.

2.	Grafana의 $__timeFilter 매크로로 Timestamp가 지정된 시간 범위에 속하는지 확인합니다.

3.	ServiceName이 주어진 serviceName 값들 중 하나와 일치하는지 확인합니다.
●	시간을 분 단위로 그룹화하고, 해당 시간에 얼마나 많은 로우(요청)이 있는지 계산합니다.
●	동일한 otel_traces 테이블에서 데이터를 선택하고, 동일한 조건과 그룹화를 적용합니다. 다만, 여기서는 ServiceName 조건이 적용되지 않습니다.
●	주 쿼리 시작. 두 CTE의 결과를 조합하여 각 서비스의 요청 비율을 계산합니다.
●	두 CTE (RequestCounts와 TotalRequestCounts)를 time 컬럼을 기준으로 JOIN합니다.
