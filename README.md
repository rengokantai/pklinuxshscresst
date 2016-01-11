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
- cp4
```
complete -p
```
some variables:
```
COMP_WORDS
COMP_CWORD
COMPREPLY
```
- cp5
```
printenv SHELL
env
set| grep var
```
For path, we do not need to export, just append
```
PATH = $PATH:/......
```


- cp6
```
move -n src dest  # donot overwrite
```
just memorize
```
for i in /etc/profile.d/*.sh; do
  if [ -r $i]; then
  if[ "${-#*i}" != "$-"]; then
  . "$i"
  else
```
```
echo $HISTFILE
echo $HISTFILESIZE
echo $HISTSIZE
```
prompt history
press ! follow by other chars
!? --> search previous commands

suspend a running command:
press ctrl z

to send a suspended task to continue running in background:
```
bg
```
listing background tasks:
```
jobs
```
"+" means the job is ```fg``` or ```bg```
"-" means the job will become default job if current default job terminates
```
job -r #background jobs
job -s #suspended jobs
job jobid
```

delete all stopped jobs
```
disown
disown -r #delete all running tasks
disown -a #delete all tasks
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
ps
```
ps -e u | wc -l # choose all progress and user-oriented format -e = -A
ps u -u root
```
get tty
```
ps t
```
get by command name
```
ps u -C firefox, bash
```
pstree with pid
```
pstree -p (pid)
```
byuser
```
psuser -pu (pid)
```
nice
```
nice -n 10 psname &
nice --10 paname
```
change running ps -> renice
```
renice  -n -5 -u username
renice -n 2 -p 1234 5678
```
signal convert
```
kill -l 9 #SIGKILL
```
trap (ex, in shell script)
```
trap "rm file" SIGTERM SIGQUIT SIGABRT   # (when these signals trigger, rm file will execute)
```

ipcs
```
ipcs -m -p
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

