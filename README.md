и так, это мини-гайд как сделать стрим, консьюмера, и бакеты. начнем!

если до сих пор не установил `nats-server`, тогда самое время это сделать!
перейди по этой ссылке: https://github.com/nats-io/nats-server/releases/ и скачай самую новую версию. после этого, нужно скачать [nats](https://github.com/nats-io/natscli/releases) и [nats top](https://github.com/nats-io/nats-top/releases) для полной красоты. после всего этого, нужно создать файл server.conf и написать туда:
```
jetstream {
    store_dir='/home/{user}/nats/'}
http_port: 8222
```
сохранить и написать команду `nats-server -c server.conf` в той же директории, где создал файлик `server.conf`

если всё получилось, тогда должна быть примерно следующая картина:
![img.png](img.png)

если появилась ошибка или еще что-то, милости прошу идти в google.com

теперь создай новую вкладку в терминале и напиши туда `nats stream add` с таким конфигом:
![img_1.png](img_1.png)

после этого, нужно создать consumer. напиши команду `nats consumer add` с следующим конфигом:
![img_2.png](img_2.png)

иногда нужно создать бакеты. чтобы это сделать, напиши команду: `nats kv add name —history=5 —storage=file` . эта команда создаст бакет с именем `name`(имена бакетов, которые нужно создать я буду указывать в README.md)

бывают случаи, когда нужно запустить несколько сервисов для работы с `nats`. команды(или ссылки) я оставлю ниже:

скачать grafana:
```
sudo apt-get install -y apt-transport-https
sudo apt-get install -y software-properties-common wget
sudo wget -q -O /usr/share/keyrings/grafana.key https://packages.grafana.com/gpg.key
echo "deb [signed-by=/usr/share/keyrings/grafana.key] https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

скачать prometheus-nats-exporter: [ссылка](https://github.com/nats-io/prometheus-nats-exporter/releases)

скачать prometheus:
```
sudo apt-get install prometheus
```

наш чат: https://t.me/nats_py
на этом, пожалуй, всё. спасибо за внимание!
