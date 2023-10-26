## Traces

otel_traces 테이블에서 각 TraceId 별로 최초의 타임스탬프, 서비스 이름 및 전체 지속 시간을 계산하고, 그 결과를 지속 시간에 따라 내림차순으로 정렬하여 상위 100개만 반환합니다.

●	각 TraceId 별로 Timestamp 컬럼의 최소값을 계산하고, 그 값을 timestamp라는 이름으로 반환합니다.

●	argMin 함수는 첫 번째 인수의 값을 반환하는데, 그 값은 두 번째 인수의 최소값에 해당합니다. 여기서는 각 TraceId 별로 가장 이른 Timestamp에 해당하는 ServiceName 값을 반환하며, 그 값을 Service Name이라는 이름으로 가져옵니다.

●	Grafana의 매크로 $__conditionalAll를 사용하여, TraceId가 주어진 변수 trace_id 값들 중 하나와 일치하는지 확인합니다.

●	Grafana의 $__timeFilter 매크로를 사용하여, 대시보드의 현재 시간 범위에 Timestamp가 포함되는지 확인합니다.
