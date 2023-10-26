## Memory Usage
otel_metrics_sum 테이블에서 메모리 관련 메트릭을 선택하고, 해당 메트릭의 시간당 평균 사용량을 계산한 뒤, 그 결과를 시간과 메트릭 이름으로 정렬하여 반환합니다.

●	concat 함수는 여러 개의 문자열을 연결하는 함수입니다. 여기서는 MetricName의 값과 ResourceAttributes에서 'service.name'에 해당하는 값을 연결하며, 그 사이에 괄호로 서비스 이름을 묶습니다. 예: "memoryUsage (myService)". 이 결과를 Metric이라는 이름으로 반환합니다.

●	Value 컬럼의 평균 값을 계산하며, 이 평균값을 Avg_MEMORY_Usage라는 이름으로 반환합니다.

●	WHERE 절은 특정 조건을 만족하는 로우만 선택하는데 사용됩니다. 여기서는 MetricName 컬럼의 값 중 'memory' 문자열을 포함하는 로우만 선택됩니다.
