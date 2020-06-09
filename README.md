Test task.

docker-compose up -d
Network 172.20.128.

sipp 172.20.128.2 -i 172.18.0.1 -sf uac_noheader.xml -aa -inf res.csv -d 100 -l 1 -r 1 -rp 1000 -trace_msg -trace_err -trace_stat

