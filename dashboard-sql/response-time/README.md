## Response Times

otel_traces 테이블에서 주어진 조건을 만족하는 서비스의 평균 지속 시간을 시간 간격별로 계산하고 그 결과를 반환합니다.

●	$__timeInterval(Timestamp)는 Grafana에서 제공하는 매크로로, Timestamp를 지정된 시간 간격으로 그룹화합니다. 이를 time이라는 이름으로 가져옵니다.

●	Duration 컬럼의 평균 값을 계산합니다. 반환된 결과의 컬럼 이름은 공백입니다 (이것은 특이한 부분입니다; 일반적으로 반환된 컬럼에 의미 있는 이름을 제공합니다).

●	Grafana의 매크로 $__conditionalAll를 사용하여, TraceId가 주어진 변수 trace_id 값들 중 하나와 일치하는지 확인합니다.

●	$__timeFilter(Timestamp)는 Grafana의 매크로로, 현재의 대시보드 시간 범위에 Timestamp가 포함되는지를 확인합니다.

●	$__fromTime과 $__toTime는 Grafana에서 제공하는 매크로로, 대시보드의 시작 및 종료 시간을 나타냅니다. 이 조건은 선택된 시간 범위 내의 데이터만을 필터링합니다.

●	ServiceName이 주어진 변수 serviceName 값들 중 하나와 일치하는지 확인합니다.
●	결과를 시간 (time)과 ServiceName 별로 그룹화합니다.
