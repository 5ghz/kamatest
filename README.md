Test task.

Для проверки надо выполнить команду<br>
```docker-compose up -d```<br>
При запуске создаётся сеть<br>
Network: 172.20.0.0/16<br>
После этого запускаются два контейнера:<br>
app_asterisk 172.20.128.3<br>
app_kamailio 172.20.128.2<br>

Для тестирования надо запускать sipp <br>
uac_header.xml есть заголовок X-SomeHeader<br>
uac_noheader.xml нет заголовока X-SomeHeader<br>

```sipp 172.20.128.2 -i 172.18.0.1 -sf uac_header.xml -aa -inf res.csv -d 100 -l 1 -r 1 -rp 1000 -trace_msg -trace_err -trace_stat```<br>

```sipp 172.20.128.2 -i 172.18.0.1 -sf uac_noheader.xml -aa -inf res.csv -d 100 -l 1 -r 1 -rp 1000 -trace_msg -trace_err -trace_stat```<br>

