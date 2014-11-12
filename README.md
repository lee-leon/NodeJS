NodeJS
======

developing on NodeJS



In order to debug Nodejs remotely, you should modify some lines in source code. Here is my sitruation:
      1，NodeJS is installed on Centos
      2，Eclipse(Debug tool for Nodejs) is installed in Windows 8 with a plugin named Chrome V8 VM(To 
         install this plugin, you can use the "Help->install new software" functionality of eclipse).

We must know that NodeJs is originally bined to localhost at port 5858 in debug mode. So, if you want to 
debug the source code in other machine(Here I want ot debug it in Windows 8), you should download the 
source code of NodeJS and modify the following line in file ./deps/v8/src/platform-posix.cc:
            addr.sin_family = AF_INET;
            addr.sin_addr.s_addr = htonl(INADDR_LOOPBACK); #### Here, change INADDR_LOOPBACK to INADDR_ANY
            addr.sin_port = htons(port);
Then, remake the source code. You can enjoy the remote debugging now. Have fun.
