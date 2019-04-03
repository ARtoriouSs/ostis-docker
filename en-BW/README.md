# Dockerized ims.ostis

This is the OSTIS instructions for writing in the [Docker](https://habr.com/ru/post/309556/ "Docker") container. 
 First of all, why it is needed: If for some reason the system does not start in the installed OS, you can run it in an isolated container, you just need to install Docker and follow the instructions below. In the same way, you can run a superintelligent system from Windows. This is similar to running on a virtual machine, but it requires less memory and is much faster than installing a full virtual machine. Plus, it should work well, just 99% and no manual settings. So:

## Install and Run

**Step 0**

First you need to install Docker:

- [For Linux](https://www.digitalocean.com/community/tutorials/docker-ubuntu-16-04-ru "Установка Docker на Ubuntu")

- [For macOS](https://docs.docker.com/docker-for-mac/install/ "Установка Docker на macOS")

- [For Windows 10](https://hub.docker.com/editions/community/docker-ce-desktop-windows "Installing Docker on Windows 10") or [for old Windows](https://docs.docker.com/toolbox/overview/ "Docker installation on old Windows")

Still, if there is Linux, it is better to do everything there. If the installation of the links is something unclear, you can just google it, everything will be painted.

Then just follow one of the instructions below. For shindovs, it is better to use a bash emulator [such as GitBash](https://gitforwindows.org/ "Gitbash") . In CMD or PowerShell is also possible. But do not need :)

There are two chairs here: to incline the repository and run scripts, it is much easier and you don’t need to think too much, or simply execute commands consistently, you don’t need to think in principle, just copy-paste, but it's still easier to get confused. But you do not need to tilt the repository, and you can better understand what is happening.

To make it easier to break into two separate instructions:

- [Simple](https://github.com/ARtoriouSs/docker-ims.ostis/blob/master/script_instruction.md "Scripting method") . IMHO it's better, not for nothing that I did it :)

- [Also simple, but not quite](https://github.com/ARtoriouSs/docker-ims.ostis/blob/master/command_instruction.md "Way with teams") .

If you want to know what is happening, then in the second instruction there is a description of each step.

## Troleshuting

All the problems found and their possible solutions will be [here](https://github.com/ARtoriouSs/docker-ims.ostis/blob/master/troubleshooting.md "The solution to all your life problems") .

## Contribution

Well, everything is as usual here, it’s open sour baby, the current is hardly necessary for someone:

- Fork it.

- Make your changes.

- Open pull request.

Or not open and keep the fork yourself, I don’t care so much :)

**PS** The author of the idea is [Masha](https://github.com/idealasgas "Github Masha") :)
