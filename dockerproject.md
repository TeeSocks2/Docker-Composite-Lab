# Docker Project

## Part 1 (Docker Installation)

### Part 1.1 (Picking Your OS)

Before going through the process of installing Docker, you need to figure out what OS you are going to install Docker on. For me, I ended up sticking with Ubuntu. The rest of this guide is going to follow how I installed an Ubuntu VM, and then installed Docker on said VM.

### Part 1.2 (The Right Version Ubuntu)

Unfortunately, for the process I am using to install Docker, you can't just use any version of Ubuntu. For the installation process I am going to go in detail on in later parts of this document, I installed Docker on Ubuntu LTS version 20.04.6.

- I am certain there are other versions of Ubuntu LTS that let you install Docker the way I did it, however, I am not sure what versions of Ubuntu those are besides LTS 20.04.6. So, for simplicity's sake, the rest of this document will be going over the Docker installation process with version 20.04.6 in mind.

Go into your prefered search engine and type "Ubuntu LTS version 20.04.6." CLick on the first link you see that pops up in your search engine. Scroll down the page until you see the iso file for LTS 20.04.6. When you click the link, it should automatically install the iso file for you. Once the iso file finishes installing, open up VmWare Workstation and begin setting up a VM for Ubuntu.

### Part 1.3 (Setting Up the VM)

Open up VMWare Workstation and create a new virtual machine. Select "Installer disc image file (iso)" and browse until you find wherever your recently installed iso file.

- Usually, it should be in your downloads folder, or wherever you set most of your downloaded files to go.

On the next screen, VMWare should ask you to put down a few credentials for your VM. Put down whatever you like for these credentials, so long as you set your password to something you can easily remember and type down. If you want to, rename your VM machine.

On the next screen, make sure maximum disk size is set to (at least) 25GB. Also makse sure that you are splitting your virtual disk into multiple files. On the next screen, make sure your memory is set to (again, at least) 2.5GB, and that you have 2 CPU cores set for your VM.

Once you have done all of those afforementioned steps, all you need to do to login to your Ubuntu VM is start it up, and then type down the password that you put down when you were setting your credentials for the Ubuntu VM.

### Part 1.4 (Checking & Updating Your Ubuntu Terminal)

Before continuing with this step, please __DO NOT UPDATE YOUR CURRENT VERSION OF UBUNTU TO 21 OR ANYTHING HIGHER,__ because this will end up messing up the entire installation process, and you will have to start over from the very beginning.

Go into your Ubuntu terminal and check what may need to be updated. Go ahead and upgrade everything that your terminal just listed.

- You can check for updates by typing "sudo apt-get update" and you can upgrade everything in your terminal by typing "sudo apt-get upgrade."

Once you have upgraded every package, begin installing Docker onto your VM.

### Part 1.5 (Docker Installation)

Before I begin, it should be noted that I chose to install Docker like it were included in an apt repository.

Type `sudo apt-get update` to, once again, check if there are any available updates.

- If there are, install them using the `sudo apt-get upgrade` command.

After this, simply install Docker by typing the following command into your terminal: `sudo apt-get install docker.io`

### Part 1.6 (Making Sure It Works)

Check the status of Docker in your terminal.

- Do this by running the following command: `sudo service docker status`

If it says that Docker is inactive, start running docker in your Terminal.

- This can be done with the following command: `sudo service docker start`

Type the following command into the terminal: `sudo docker run hello-world`

If you run the afforementioned commannd and it works as intended, then congratulations! You have successfully installed Docker onto your Ubuntu VM! Now, I'm going to show you how to install WordPress using Docker on your Ubuntu VM.

## Part 2 (OpenVAS Installation)

### Part 2.1 (Container Installation)

Before we can make a container for OpenVAS, we first need to install one.

Run the following command in your Linux terminal to install a container: `sudo docker run -d -p 443:443 --name openvas mikesplain/openvas`

After you run this command, it should take you at least a few minutes to successfully install the container, so wait to do anything next until then.

### Part 2.2 (Local Host Connection)

After your Docker container has finally finished installing, go into your Firefox browser and type the following url in your search bar: "https://localhost/"

If the page loads correctly, click the advanced optiob, scroll down, and click accept the risk and continue.

- You should know if the page loaded correctly if you get a screen that says "Warning: Potential Security Risk Ahead."

You should make it to a login page. Once you do, enter "admin" for both the username and the password.

### Part 2.3 (Making a Target)

When you make it to the Greenbone page, click on "Configuration" and then click on "Targets." When you make it to the "Targets" page, click on the little star icon and create a new target.S

From here, specify the name of the target and (this is the most important part) specify the ip address of said target.

### Part 2.4 (Making a Task)

- You should the ip address of something that actually exists and not something made up.

After you have made a target, go to the "Scans" dropdown and click on "Tasks." Again, click on the star icon. (This will create a new task this time, instead of a new target) Specify the name of the task, and make sure your scanner is on the "OpenVAS Default" option. Finally, create the task.

After you have created your task, press the little play button near the bottom right of the screen to start the task. From here, keep refreshing the page until the task until it is finished.

If you want to see the result of your task, go to the "Scans" dropdown and click on "Reports." From there you should be able to look at all the tasks you've run and see things related to the task you've run, such as its status and its severity.

Congratulations, you have successfully installed OpenVAS with Docker on an Ubuntu VM!!!

## Error Documentation

### Part 1

#### Part 1.2

When I first tried to install Docker on an Ubuntu VM, the first form of Ubuntu I tried was a version of Ubuntu 22 LTS. This ended up not working for me, so instead I tried using an earlier version of Ubuntu, hence, Ubuntu 20.04 LTS.

#### Part 1.3

When I first tried to install OpenVas via Docker, my VM was so slow because 20GBs of data and 2GB of memory was not enough. I had to allocate more data to my VM, so I had to change from 20GBs to 25GBs, and 2GBs to 2.5GBs.

### Part 2

#### Part 2.2

When I tried using the local host link, it would never work. Still, I am unsure why this was the case, but eventually I got the link to work by just starting the process over again.
