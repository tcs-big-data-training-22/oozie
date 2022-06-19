- Check Version
```
oozie version
```

- To check the status of the Oozie system
```
ifconfig
oozie admin -oozie http://10.0.0.13:11000/oozie -status
```

- Switch User
```
ssh u20@localhost
```

- Put Oozie files to HDFS
```
cd
git clone https://github.com/tcs-big-data-training-22/oozie
cd ~/oozie/PythonShell
hadoop fs -mkdir /user/$USER/oozie
hadoop fs -rm -r /user/$USER/oozie/python-shell
hadoop fs -mkdir /user/$USER/oozie/python-shell
hadoop fs -put workflow.xml /user/$USER/oozie/python-shell
hadoop fs -put *.py /user/$USER/oozie/python-shell
hadoop fs -chmod 777 /user/$USER/oozie/python-shell/*
hadoop fs -ls /user/$USER/oozie/python-shell
```

- Validating a Workflow XML −
```
oozie validate workflow.xml
```


- Running Workflow
```
ifconfig
export OOZIE_URL=http://10.0.0.13:11000/oozie
oozie job -config job.properties -submit
```

- Info about your job
oozie job -info 0049130-161020154537822-oozie-oozi-C

- See running workflows
oozie jobs -jobtype=WF -filter status=RUNNING
