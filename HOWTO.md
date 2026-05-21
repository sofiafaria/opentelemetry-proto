#How to generate trace proto files
1 - Run postCreateCommand
2 - Create a request-trace.textproto using the schema displayed in the example folder
3 - Execute command in shell to convert to .pb file:
protoc -I . \
  --encode=opentelemetry.proto.collector.trace.v1.ExportTraceServiceRequest \
  opentelemetry/proto/collector/trace/v1/trace_service.proto \
  < request-trace.textproto \
  > request-trace.pb

4 - Use the request-trace.pb file in HTTP request using:
curl --location 'https://LS-SPDYNGW03.hluz.ess.local:443/e/ebf69986/api/v2/otlp/v1/traces' \
--header 'Content-Type: application/x-protobuf' \
--header 'Authorization: Api-Token {Token}' \
--data-binary '@request-trace.pb'


#How to generate logs proto files
1 - Run postCreateCommand
2 - Create a request-log.textproto using the schema displayed in the example folder
3 - Execute command in shell to convert to .pb file:
protoc -I . \
  --encode=opentelemetry.proto.collector.logs.v1.ExportLogsServiceRequest \
  opentelemetry/proto/collector/logs/v1/logs_service.proto \
  < request-log.textproto \
  > request-log.pb

4 - Use the request-trace.pb file in HTTP request using:
curl --location 'https://LS-SPDYNGW03.hluz.ess.local:443/e/ebf69986/api/v2/otlp/v1/logs' \
--header 'Content-Type: application/x-protobuf' \
--header 'Authorization: Api-Token {Token}' \
--data-binary '@request-log.pb'