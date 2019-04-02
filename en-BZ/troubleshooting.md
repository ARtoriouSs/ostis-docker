# Here will be described how to solve problems with the launch of the system

If the solution to your problem is not in this document, but you have it, it would be nice to add it to this file and open the pull request :)

## On Windows

- When installing a docker problem with the lack of virtualization

We look for example [here](https://support.qnap.ru/hc/ru/articles/360000723294-%D0%9A%D0%B0%D0%BA-%D0%B2%D0%BA%D0%BB%D1%8E%D1%87%D0%B8%D1%82%D1%8C-%D0%BF%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%BA%D1%83-%D0%B0%D0%BF%D0%BF%D0%B0%D1%80%D0%B0%D1%82%D0%BD%D0%BE%D0%B9-%D0%B2%D0%B8%D1%80%D1%82%D1%83%D0%B0%D0%BB%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D0%B8-Intel-VTx-AMD-SVM-%D0%B2-%D1%81%D0%B5%D1%82%D0%B5%D0%B2%D0%BE%D0%BC-%D1%85%D1%80%D0%B0%D0%BD%D0%B8%D0%BB%D0%B8%D1%89%D0%B5-QNAP-) or just google.

- SECURITY WARNING

```
SECURITY WARNING: You are building a Docker image from Windows against a non-Win dows Docker host. All files and directories added to build context will have '-r wxr-xr-x' permissions. It is recommended to double check and reset permissions f or sensitive files and directories.
```

This is just a warning you can ignore.

- proxy input / output error

```
C:\Program Files\Docker\Docker\Resources\bin\docker.exe: Error response from daemon: driver failed programming external connectivity on endpoint confident_elbakyan (a0c50014a5332bdba02aa202209b2b8cb3ad083c15698cddb42ab723cd4cсdc9): Error st arting userland proxy: mkdir /port/tcp:0.0.0.0:8000:tcp:172.17.0.2:8000: input/output error.
```

From the bottom right, look for the docker icon (whale), poke it with the right button, poke Restart there, wait for the restart and try again, it should work.

## On linux

Linux is perfect, no problems :)

## Run without Internet

This can be done only locally and without making a pull from the dockhab. To do this, run the script / command in noupdate mode without the --pull parameter. If this is a script, then you need to open it and remove this parameter.
