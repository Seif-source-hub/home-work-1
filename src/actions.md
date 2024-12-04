`1.` Запуск контейнеров Docker:
```shell
docker compose up -d
```

`2.` Вывод списка всех контейнеров Docker (включая остановленные):
```shell
docker compose ps -a
```

`3.` Получаем список Топиков которые есть в Kafka брокере, доступном по адресу kafka:9092 и находящемся внутри контейнера Docker с именем kafka:
```shell
docker exec -ti kafka /usr/bin/kafka-topics --list --bootstrap-server kafka:9093
```

`4.` Создаем новый топик "vowels"
```shell
docker exec -ti kafka /usr/bin/kafka-topics --create --topic vowels --bootstrap-server localhost:9093
```

`5.` Создаем новый топик "consonants"
```shell
docker exec -ti kafka /usr/bin/kafka-topics --create --topic consonants --bootstrap-server localhost:9093
```

`6.` Отправляем сообщение "vowels": появляется консоль ввода сообщений, вводим сообщение одно за другим, разделяя Enter и в конце нажимаем в Win ctrl+D (в MacOS: control+C)
```shell
docker exec -ti kafka /usr/bin/kafka-console-producer --topic vowels --bootstrap-server kafka:9093
```

`7.` Отправляем сообщение "consonants": появляется консоль ввода сообщений, вводим сообщение одно за другим, разделяя Enter и в конце нажимаем в Win ctrl+D (в MacOS: control+C)
```shell
docker exec -ti kafka /usr/bin/kafka-console-producer --topic consonants --bootstrap-server kafka:9093
```

`6.` Получить сообщения vowels
```shell
docker exec -ti kafka /usr/bin/kafka-console-consumer --from-beginning --topic vowels --bootstrap-server localhost:9093
```

`7.` Получить сообщения consonants
```shell
docker exec -ti kafka /usr/bin/kafka-console-consumer --from-beginning --topic consonants --bootstrap-server localhost:9093
```