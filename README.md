# kafka-cluster-ssl

이 저장소는 kafka-cluster-ssl에 대한 저장소입니다.

## SSL 보안 클러스터 설정을 위한 필요한 인증서 생성

- **secrets** 디렉토리로 이동합니다.

- 아래의 명령어를 실행합니다.

```script
sh create-certs.sh
```

## SSL 보안 환경에서 메시지 생성/소비

- 주제에 메시지를 생성합니다.

```
docker exec --interactive --tty kafka1  \
kafka-console-producer --bootstrap-server localhost:9092 \
                       --topic test-topic \
                       --producer.config /etc/kafka/properties/producer.properties

```

- 주제에서 메시지를 소비합니다.

```
docker exec --interactive --tty kafka1  \
kafka-console-consumer --bootstrap-server localhost:9092 \
                       --topic test-topic \
                       --from-beginning \
                       --consumer.config /etc/kafka/properties/consumer.properties
```


```agsl
docker exec --interactive --tty kafka1  \
kafka-console-consumer --bootstrap-server localhost:9092 \
                       --topic library-events \
                       --from-beginning \
                       --consumer.config /etc/kafka/properties/consumer.properties

```