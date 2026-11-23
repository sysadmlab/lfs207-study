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
3. data.tar.xz <br>  
<img width="689" height="135" alt="Screenshot From 2026-11-19 14-51-35" src="https://github.com/user-attachments/assets/3a214e70-42f4-4722-9f38-5748de282f9e" />  
The file **debian-binary** has the text **2.0** in it. This file tells **dpkg** which version of the **.deb** format this package uses. <br>
<img width="704" height="277" alt="Screenshot From 2026-11-22 20-31-14" src="https://github.com/user-attachments/assets/19706c8f-f90a-44b5-b7de-5defb112a792" />
The file **control.tar.xz** contains the metadata of the package and scripts those that **dpkg** reads and stores in its database.
The file **data.tar.xz** contains the actual binaries that are copied to the system.

## Downloading a source package  
To download a source package, the command is **apt-get source (package_name)**.  
However, this command did not work as such in my Ubuntu Server VM.  
On further research, I understood that for that command to work, I need to enable **deb-src** "source repositories" in the list of source queried by **apt**.  
To achieve that, using elevated privileges, I must open the file **/etc/apt/sources.list.d/ubuntu.sources**.  
Then I must include **deb-src** in the **Types** for both the block of text present in this file: as shown in the image below <br>  
<img width="1050" height="273" alt="image" src="https://github.com/user-attachments/assets/b1ecdf3b-d630-47db-a46a-9ef5e3bc0518" />
Then run the command **sudo apt update** to refresh the repositories.  
Now executing the command **apt-get source net-tools** downloads the source packages for **net-tools**.  

### Contents of a source package  
The **net-tools** source package I downloaded consists of three files:  
1. net-tools_2.10-0.1ubuntu4.4.debian.tar.xz  
2. net-tools_2.10-0.1ubuntu4.4.dsc  
3. net-tools_2.10.orig.tar.xz <br>  

The file **net-tools_2.10.orig.tar.xz** is the source code as published by the developers of the package - also known as **upstream** package.  
The file **net-tools_2.10-0.1ubuntu4.4.debian.tar.xz** contains Debian and Ubuntu's changes and instructions to build from the **upstream** source code package.  
The file **net-tools_2.10-0.1ubuntu4.4.dsc** is the **Debian Source Control** file which has information about the other two archives (tarballs), what they do, and ensure their file integrity.  

The **upstream** source code tarball and the ubuntu.debian tarball could have been published/updated at different times. <br>  
<img width="889" height="522" alt="Screenshot From 2026-11-23 08-14-12" src="https://github.com/user-attachments/assets/d9a6d2ef-ec74-42e0-89d3-2d5ae1750858" />  
The image above shows that the source code was published earlier and the ubuntu.debian file was re-published much later.  
