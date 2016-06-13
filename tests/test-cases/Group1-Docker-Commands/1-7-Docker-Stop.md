Test 1-7 - Docker Stop
=======

#Purpose:
To verify that docker stop command is supported by VIC appliance

#References:
[1 - Docker Command Line Reference](https://docs.docker.com/engine/reference/commandline/stop/)

#Environment:
This test requires that a vSphere server is running and available

#Test Steps:
1. Deploy VIC appliance to vSphere server
2. Issue docker create busybox sleep 30 to the VIC appliance
3. Issue docker stop <containerID> to the VIC appliance
4. Issue docker start <containerID> to the VIC appliance
5. Issue docker stop <containerID> to the VIC appliance
6. Issue docker start <containerID> to the VIC appliance
7. Issue docker stop -t 2 <containerID> to the VIC appliance
8. Issue docker stop fakeContainer to the VIC appliance

#Expected Outcome:
* Steps 2-8 should each complete without error, and the response should be the containerID
* Step 5 should take 10 seconds to complete
* Step 7 should take 2 seconds to complete
* Step 8 should respond with the following error message:
```
Failed to stop container (fakeContainer): Error response from daemon: No such container: fakeContainer
```

#Possible Problems:
None