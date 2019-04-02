# Detailed start-up instructions without cloning the repository

Below is a brief instruction if details are not needed. There is also a [simpler](https://github.com/ARtoriouSs/docker-ims.ostis/blob/master/script_instruction.md "Instructions with scripts") version.

**Step 1**

First you need to throw off everything that should be in the database into one any folder, then go to this folder in the terminal, these files will be copied to the container (most likely it will be the kb folder):

```bash
cd ostis/kb # или cd абсолютно/любая/папка/в/которой/лежат/файлы/базы
```

**Important!** This folder should not be completely empty. If you just want to check whether it will work, you can create any file: `touch .keep` .

**Step 2**

We collect image from Dockerfile'a in this repository. Clone it yourself is not necessary. 
 There are two options: the first one will strip my [image](https://cloud.docker.com/u/artorious/repository/docker/artorious/ostis "Dockerhub") from DockerHub and update all the submodules, the second one will not update. In the first case, the container will use the latest version of the system, but it happened that the repository was filled with changes that break something. For this case, there is a second option: it will almost 100% run everything as needed, but there is a chance that sometime something important will be poured on these sub modules and it will turn out that this option will deploy an irrelevant version of the system. Versions of repositories can be found [here](https://github.com/ARtoriouSs/docker-ims.ostis/blob/master/versions.md "Versions") .

After the update (or its absence), both options will copy everything that is in the current directory to the kb folder in the container, for this the previous step was needed.

Shtosh, the first version with updates:

```bash
curl https://raw.githubusercontent.com/ARtoriouSs/docker-ims.ostis/master/Dockerfile | docker build --pull --tag ostis --file - .
```

Or the second, without updates, if the first does not work:

```bash
curl https://raw.githubusercontent.com/ARtoriouSs/docker-ims.ostis/master/Dockerfile.noupdate | docker build --pull --tag ostis --file - .
```

The first time it will download about two gigs of ~ viruses ~, in subsequent launches everything will be much faster. If all is well at the end there should be lines Successfully built and Successfully tagged. On Windows, there may still be a warning about a non-windows host, this is the norm.

These commands just take the text of dockerfiles from this repository, so there’s no need to download anything. The scripts in the second version of the instructions use local dokerfiles.

**Step 3**

Now we have a locally created image called ostis, this can be checked by doing `docker images` , there should be two artorious / ostis images with an empty ostis from DockerHub and ostis from a docker file, which now needs to be run, exported port 8000:

```bash
docker run -p 8000:8000/tcp ostis bash -c "./run.sh"
```

This command will create a container from the created ostis image, redirect the container port 8000 to the local machine, and run the run.sh script inside this container, which will simply run redis-server, restart_sctp.sh and run_scweb.sh. All output of these commands will be visible in the console, that is, if there are any errors when building the database, they can be found there as usual. After that, you need to wait a bit until everything starts up there and everything, now OSTIS listens to localhost: 8000, you can go there in the browser and poke it, all copied files should be available in the search.

**Step 4 or how to chop it all out didn’t eat the whole memory after a few restarts**

Exit the container by pressing ctrl + C and writing `exit` . This may not work in some shells, if so, open a new terminal (tab) and write:

```bash
docker rmi -f $(docker images -f "dangling=true" -q) & docker rmi -f ostis & docker rm -f $(docker ps -aq)
```

The command must be executed in any case, even if ctrl + C worked. It will remove all containers and the collected image. If you really want to check, then `docker ps -a` will show all the containers, they should be absent, and `docker images` will show all the images, only the basic artorious / ostis image should remain there. If this is all too scary (or useless) and will not be used anymore, then you can do the `docker system prune` , it will delete all the images and containers in general so that they do not take up memory. It is worth remembering that each created container and image zanmany memory, and if you do not perform step 4, it will be byaka: (

Now you can make changes to your files and do it all over again.

Also, after the second step, you can check if the files are in kb by doing the following:

```bash
docker run ostis bash -c ./show_kb.sh
```

If something went wrong according to the plan and it’s broken, you can see if there is a solution [here](https://github.com/ARtoriouSs/docker-ims.ostis/blob/master/troubleshooting.md "Shooting on problems") .

**If everything looks scary and incomprehensible, then here is the same but without explanation:**

We collect:

```bash
curl https://raw.githubusercontent.com/ARtoriouSs/docker-ims.ostis/master/Dockerfile | docker build --pull --tag ostis --file - .
```

Run:

```bash
docker run -p 8000:8000/tcp ostis bash -c "./run.sh"
```

We look what, 
 We cut down:

```bash
docker rmi -f $(docker images -f "dangling=true" -q) & docker rmi -f ostis & docker rm -f $(docker ps -aq)
```

We make changes to the database, reassemble, launch, cut down, collect, launch, cut down, collect, launch, cut down, collect, launch, cut down, collect, start, cut down, collect, start, cut down, collect we start, we cut down, we collect, we start, we cut down ...
