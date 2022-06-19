- Check Version
```
oozie version
```

- To check the status of the Oozie system
```
ifconfig
oozie admin -oozie http://localhost:11000/oozie -status
```

- Switch User
```
ssh u20@localhost
```

- Put Oozie files to HDFS
```
cd
git clone https://github.com/tcs-big-data-training-22/oozie
cd ~/oozie/MapReduce
hadoop fs -mkdir /user/$USER/oozie
hadoop fs -rm -r /user/$USER/oozie/MapReduce
hadoop fs -mkdir /user/$USER/oozie/MapReduce
hadoop fs -put workflow.xml /user/$USER/oozie/MapReduce
hadoop fs -put input-data /user/$USER/oozie/MapReduce/input-data
hadoop fs -put lib /user/$USER/oozie/MapReduce/lib
hadoop fs -ls /user/$USER/oozie/MapReduce/
hadoop fs -ls /user/$USER/oozie/MapReduce/input-data
hadoop fs -ls /user/$USER/oozie/MapReduce/lib
hadoop fs -chmod 777 /user/$USER/oozie/MapReduce/*
hadoop fs -ls /user/$USER/oozie/MapReduce
```

- Validating a Workflow XML −
```
oozie validate workflow.xml
```

- Check the port number at which NameNode is listening
```
ifconfig
telnet 10.0.0.13 8020
telnet 10.0.0.14 8050
```

- Change job.properties to replace localhost with the correct ip address and port number for nameNode

- Change job.properties to replace localhost with the correct ip address and port number for jobTracker

- If required change the value of oozie.wf.application.path

- Finally, these 3 values will look something like below:
```
nameNode=hdfs://10.0.0.13:8020
jobTracker=10.0.0.14:8050
oozie.wf.application.path=/user/${user.name}/${oozieRoot}/MapReduce
```

- Running Workflow
```
ifconfig
export OOZIE_URL=http://localhost:11000/oozie
oozie job -config job.properties -run
```

- Info about your job
oozie job -info 0049130-161020154537822-oozie-oozi-C

- See running workflows
oozie jobs -jobtype=WF -filter status=RUNNING
