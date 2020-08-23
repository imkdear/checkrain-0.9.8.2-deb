# checkrain-0.9.8.2-deb
checkrain fort dpkg

[Tutorial] Using Project Sandcastle on Linux
Tutorial

Today Project Sandcastle is released. It allows you to use Android on your iPhone 7, 7+, iPod Touch 7 and is compatible with macOS and Linux. But, Readme is not so helpful on Linux. After 2 hours of work, i finally got it. Here is how you can do it on your PC.

I used Lubuntu but it shouldn't matter if you use other distros.


iPhone9,3 running Android 10


What you need:

- Project Sandcastle Android Release: https://projectsandcastle.org/status

- libusb-1.0-0-dev, gcc, make, git and checkra1n installed on your computer.


Tutorial:

1-) Open terminal and clone the Projectsandcastle Loader:

git clone https://github.com/corellium/projectsandcastle

cd projectsandcastle/loader


2-) Download Project Sandcastle Android Release on your PC, and extract the contents to ProjectSandcastle Loader folder. It should be in your Home folder.


3-) Now you need to send the 'isetup' file. You have two choices:

- Connect to your phone via SSH and send the file with scp to /tmp directory

- Or upload the file to somewhere (i used Telegram), download it on your iPhone and put the file to /tmp via Filza. i used this method.


4-) We need to change permission of the isetup file and execute it. in terminal enter:

chmod 755 /tmp/isetup && /tmp/isetup

You can use MTerminal on this step if you went with second option of 3rd step. Do not forget to enter "su" first, otherwise it will give permission error


5-) You need to compile the Loader. Normally you need to enter:

sudo make && make install

But for some reason makefile does not compile the load-linux.c, it gives libusb errors. So use these commands if you have errors:

gcc load-linux.c -o load-linux -lusb-1.0

chmod +x load-linux


6-) We need to boot our iPhone into pongoOS to launch Android. Open another terminal and enter:

sudo checkra1n -cp


7-) When pongoOS boots successfully, switch to the previous terminal and enter:

sudo ./load-linux Android.lzma dtbpack


and your iPhone should boot into Android!
