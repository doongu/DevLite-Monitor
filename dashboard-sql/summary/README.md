## Summary

otel_traces 테이블에서 각 서비스의 지속 시간에 대한 평균 및 표준 편차를 계산하고 그 결과를 서비스 이름에 따라 오름차순으로 정렬하여 반환합니다.

●	ServiceDurations라는 CTE를 정의합니다.

●	또 다른 CTE, ServiceStats를 정의합니다.

●	ServiceDurations CTE에서 ServiceName 별로 Duration 컬럼의 평균값을 계산합니다. 그 결과는 Avg_Duration이라는 이름으로 반환됩니다.

●	각 Duration 값에서 평균 지속 시간(Avg_Duration)을 뺀 뒤, 그 차이의 제곱을 계산합니다. 이후 그 값들의 합계를 샘플 수(COUNT(*))로 나누고, 그 결과의 제곱근을 취하여 표준 편차를 계산합니다.

●	ServiceDurations CTE와 ServiceStats CTE를 ServiceName 컬럼을 기준으로 조인합니다.

●	결과를 s.ServiceName 및 Avg_Duration 별로 그룹화합니다.

