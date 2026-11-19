# dpkg Basics  
dpkg is a package management system used in Debian Linux and in derivatives of Debian.  
Debian-based systems have two levels of package management tools:  
1. dpkg - a low-level tool which works only with **.deb** files on **local disk**.  
   its database is located at **/var/lib/dpkg**  
   dpkg knows only what is installed in the system and can work based on command line input.  
   it does not download packages, it does not know about packages stored in other directories.  
   dpkg does not know about repositories, and it does not handle or resolve dependencies.  
   dpkg can unpack the file, work on the package setup files, and record the installed package in its database. <br>  

2. apt - this is the high-level tool in Debian-based distributions.  
   unlike **dpkg**, **apt** knows about repositories, works out the dependencies, downloads the **.deb** files, and hands over the installation task to **dpkg**. <br>


For this module, I have downloaded the **net-tools** package which is **not** available, by default, on my Ubuntu Server 24.04. I wanted to use the **ifconfig** tool
which has been replaced by the **ip** tool. <br>  
<img width="1250" height="719" alt="Screenshot From 2026-11-19 11-26-05" src="https://github.com/user-attachments/assets/9cea5110-df94-4f69-b144-7d77f96b7396" />  
As seen in the image above, the file I downloaded is named **net-tools_2.10-1.3_amd64.deb**. dpkg packages are named **(packagename)_(version)-(revision_number)_(architecture).deb**. <br>  

I want to observe what is inside this **.deb** file and to achieve that, I need to use the **ar** archive tool - which is not available, by default, on my Ubuntu Server VM.  
The **ar** utility is part of the **binutils** package and I will install it using **apt**.  
Using the command **ar t net-tools_2.10-1.3_amd64.deb** I can list the contents of the **.deb** file and I note three files in it:  
1. debian-binary  
2. control.tar.xz  
3. data.tat.xz <br>  
<img width="689" height="135" alt="Screenshot From 2026-11-19 14-51-35" src="https://github.com/user-attachments/assets/3a214e70-42f4-4722-9f38-5748de282f9e" />  
