## Disk Usage

●	toStartOfHour(TimeUnix) 함수는 주어진 UNIX 시간인 TimeUnix를 해당 시간의 시작 시간으로 바꾸는 함수입니다. 예를 들면, "13:45:22"는 "13:00:00"으로 변환됩니다. 그리고 변환된 값을 Time이라는 이름으로 반환합니다.

●	concat 함수는 여러 개의 문자열을 연결하는 함수입니다. 여기서는 MetricName의 값과 ResourceAttributes 딕셔너리에서 'service.name' 키에 해당하는 값을 연결하며, 그 사이에 괄호로 서비스 이름을 묶습니다. 예: "diskUsage (myService)". 이 결과를 Metric이라는 이름으로 반환합니다.

●	Value 컬럼의 평균 값을 계산하며, 이 평균값을 Avg_CPU_Usage라는 이름으로 반환합니다. (명칭이 Avg_CPU_Usage인 것은 이상한데, 아마 디스크 메트릭에 대한 평균 값을 나타내려면 Avg_DISK_Usage로 변경하는 것이 좋을 것 같습니다.)

●	WHERE 절은 특정 조건을 만족하는 로우만 선택하는데 사용됩니다. 여기서는 MetricName 컬럼의 값 중 'disk' 문자열을 포함하는 로우만 선택됩니다.
