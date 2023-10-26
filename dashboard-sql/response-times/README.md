## Response Times

otel_traces 테이블에서 주어진 조건에 따라 각 서비스의 시간별 평균 지속 시간을 계산하고 그 결과를 시간에 따라 오름차순으로 정렬하여 최대 100,000개의 로우만 반환합니다.

●	Grafana의 $__timeInterval 매크로는 주어진 Timestamp를 대시보드의 현재 시간 범위와 해상도에 맞게 반올림합니다. 그 결과를 time이라는 이름으로 반환합니다.

●	Grafana의 $__conditionalAll 매크로를 사용하여 TraceId 값이 주어진 trace_id 값과 일치하는지 확인합니다.

●	Grafana의 $__timeFilter 매크로를 사용하여 Timestamp 값이 대시보드의 현재 시간 범위 내에 있는지 확인합니다.

●	Timestamp 값이 주어진 $__fromTime 값과 $__toTime 값 사이에 있는지 확인합니다.

●	ServiceName 값이 주어진 serviceName 변수의 값 중 하나와 일치하는지 확인합니다.
