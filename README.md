#### pklinuxshscresst

- cp1
```
chsh -s /bin/bash
```
var must be declared without spaces
```
book="book" #yes
book = "book" #no
```

- cp2
```
pidof bash #2508
ls -l /proc/2508/fd
```

- cp7
go to /proc/sys/kernel check pid_max,default is 32768

get parent pid. (ppid)
```
pidof vi #8888
ps -o ppid= -p 8888
```
kill,killall
```
kill -SIGKILL 8888
killall -9 process_name
```
pkill, pgrep
```
pkill fire  #begins with fire, maybe firefox
pgrep fire
```
Exactmatch:
```
pgrep -x -l fire  #(-x = --exact)
```

- cp8
at command
```
at -f filename
at -l # =atq
at -r # =atrm
at -v time #print which job will be executed
at -c jobnumber #print job
at -m #send email
at -M #Do not send email
```
```
crontab -u user -l #diaplay crontab
crontab -i -r #interactive delete cronjob
```

systemd
```
systemctl list-unit-files | head -n 12
systemctl list-unit-files --type=service | head -n 10
```
Ex:
```
systemctl status -l NerworkManager.service
systemctl status sshd.service
```
Judge it is active/in enabled
```
systemctl is-active sshd.service
systemctl is-enabled sshd.service
```

journalctl--system log (/var/log/journal)
```
jonrnalctl -f (real time)
jonrnalctl -b (since last boot)
```

other params
```
jonrnalctl --since "1 hour ago" --until now
jonrnalctl --since 2015-07-01
jonrnalctl --since "2015-07-01 7:00:00"
```
Other scripting lang:
```
python -c ''
python3 -c ''
perl -e ''
ruby -e ''
```
In shell scrt, embed python code
```
python - <<CODE
****python code
CODE

