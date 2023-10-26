## Error rates
otel_traces 테이블에서 주어진 조건을 만족하면서 오류 상태를 가진 서비스의 오류 횟수를 시간 간격별로 계산하고 그 결과를 반환합니다.

●	$__timeInterval(Timestamp)는 Grafana에서 제공하는 매크로로, Timestamp를 지정된 시간 간격으로 그룹화합니다. 이를 time이라는 이름으로 가져옵니다.

●	Grafana의 매크로 $__conditionalAll를 사용하여, TraceId가 주어진 변수 trace_id 값들 중 하나와 일치하는지 확인합니다.

●	$__timeFilter(Timestamp)는 Grafana의 매크로로, 현재의 대시보드 시간 범위에 Timestamp가 포함되는지를 확인합니다.

●	ServiceName이 주어진 변수 serviceName 값들 중 하나와 일치하는지 확인합니다.

●	오류 상태를 나타내는 StatusCode 값이 'STATUS_CODE_ERROR'인 로우만 선택합니다.

●	결과를 ServiceName과 시간 (time) 별로 그룹화합니다.
