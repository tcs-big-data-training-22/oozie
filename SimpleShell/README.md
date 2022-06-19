- Check Version
```
oozie version
```

- To check the status of the Oozie system
```
ifconfig
oozie admin -oozie http://sandbox-hdp.hortonworks.com:11000/oozie -status
```

- Switch User
```
ssh u20@localhost
```

- Put Oozie files to HDFS
```
cd
git clone https://github.com/tcs-big-data-training-22/oozie
cd ~/oozie/SimpleShell
hadoop fs -mkdir /user/$USER/oozie
hadoop fs -rm -r /user/$USER/oozie/SimpleShell
hadoop fs -mkdir /user/$USER/oozie/SimpleShell
hadoop fs -put workflow.xml /user/$USER/oozie/SimpleShell
hadoop fs -chmod 777 /user/$USER/oozie/SimpleShell/*
hadoop fs -ls /user/$USER/oozie/SimpleShell
```

- Validating a Workflow XML −
```
oozie validate workflow.xml
```

- Check the port number at which NameNode is listening
```
ifconfig
telnet sandbox-hdp.hortonworks.com 8020
telnet sandbox-hdp.hortonworks.com 8032
```

- If required change the value of oozie.wf.application.path

- Finally, these 3 values will look something like below:
```
nameNode=hdfs://sandbox-hdp.hortonworks.com:8020
jobTracker=sandbox-hdp.hortonworks.com:8032
oozie.wf.application.path=/user/${user.name}/${oozieRoot}/SimpleShell
```

- Running Workflow
```
ifconfig
export OOZIE_URL=http://sandbox-hdp.hortonworks.com:11000/oozie
oozie job -config job.properties -run
```

- Info about your job
oozie job -info 0049130-161020154537822-oozie-oozi-C
oozie job -log 0049130-161020154537822-oozie-oozi-C

- See running workflows
oozie jobs -jobtype=WF -filter status=RUNNING
