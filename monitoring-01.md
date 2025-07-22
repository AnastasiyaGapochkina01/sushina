У команды есть приложение, написанное на nodejs. Приложение отдает свои метрики и уже подключено к prometheus. Необходимо настроить дашборд для монтиронига:
1) Обзорная панель:
- Статус приложение (up/down)
```promql
up{job="application"}
```
- RPS
```promql
sum(rate(http_requests_total[$__rate_interval])) 
```
- Error Rate
```promql
(sum(rate(http_requests_total{status=~"5..|4.."}[$__rate_interval])) 
/ 
sum(rate(http_requests_total[$__rate_interval]))) * 100
```
- Среднее время ответа
```promql
sum(rate(http_request_duration_seconds_sum[$__rate_interval])) 
/ 
sum(rate(http_request_duration_seconds_count[$__rate_interval]))
```
- Перцентили
```promql
histogram_quantile(0.50, sum(rate(http_request_duration_seconds_bucket[$__rate_interval])) by (le))
histogram_quantile(0.90, sum(rate(http_request_duration_seconds_bucket[$__rate_interval])) by (le))
histogram_quantile(0.99, sum(rate(http_request_duration_seconds_bucket[$__rate_interval])) by (le))
```
- Использование памяти
2) Детальный анализ:
- Топ медленных эндпоинтов
- Распределение ошибок
- Детализация по конкретным эндпоинтам
3) Системные метрики:
- CPU + Memory
- Event Loop + GC
- Количество потоков

Сервер мониторинга: 
84.252.141.123
