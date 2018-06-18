### 3 Steps To Build a Mentohust Package(.ipk) under Openwrt/LEDE Via Docker
##### Make life more stupid.
------
### Warning 
__Do not build as root!!!__ :hankey: :hankey: :hankey:
#### 1st. Install Docker CE && Get LEDE BUILDROOT via hub

1. [Install docker CE](https://docs.docker.com/install/ "Docker Guide")
2. Using a LEDE environment via docker 

- Run command __docker search lede__.

    You might be showed like this :
    ![image 1](https://raw.githubusercontent.com/Mon-ius/ImagePack/master/mentohust/search.png "docker search lede")

 - Choose a repository whatever you like,and type __docker pull [Name]__ pull into local.
 - Run it!

    For example,I choose __acrisliu/lede__ and  use command below:
    > `docker search`

    > `docker pull acrisliu/lede`

    > `docker run  -it acrisliu/lede`

    And you will notice where you are.
    ![image 1](https://raw.githubusercontent.com/Mon-ius/ImagePack/master/mentohust/start.png "docker run  -it acrisliu/lede")

#### 2nd. Copy Makefile into package
if you __cannot__ understand makefile,you should better learn [openwrt start](https://wiki.openwrt.org/doc/start "Openwrt WiKi") before.

1. change dir into package/,make a mentohust dictionary. __(Must Do)__

2. Download Makefile into `package/mentohust/` via __wget__ .

- wget "https://raw.githubusercontent.com/Mon-ius/mentohust-lede-makefile/mentohust/Makefile"

3. Download Makefile into `package/mentohust/` via __git clone__ .(optional)

- git clone "https://github.com/Mon-ius/mentohust-lede-makefile.git"

#### 3rd. Build mentohust package(.ipk)

1. Change dictionry back into repository started.
2. Choose your config,type `Y` or type `N`.
- make menuconfig
    you only need to change __Target System__ , __Subtarget__ , __Target profile__ .
    For example,I use __rasberrypi 3 model B__,it's target system is __'BCM270'__.
    ![image 2](https://raw.githubusercontent.com/Mon-ius/ImagePack/master/mentohust/basic.png "make menuconfig")
3. Enter into __NetWork__->__CERNET__,type `M` to export ipk.
    ![image 3](https://raw.githubusercontent.com/Mon-ius/ImagePack/master/mentohust/mentohust.png "make menuconfig->network=>cernet")
5. Save config and exit.
6. Run `make package/mentohust/clean` and `make package/mentohust/compile` that depends on your __CPU Core Numbers__ . 
7. Use find command to get __.ipk__ file,`find bin/ -name 'mentohust*.ipk'`
8. Finish!

### Conclusion 


These are all commands use in Ubuntu LTS.

> sudo apt-get update

> sudo apt-get install docker-ce

> docker pull acrisliu/lede


> docker run -it acrisliu/lede

> git clone https://github.com/Mon-ius/mentohust-lede-makefile.git

> cp mentohust-lede-makefile/mentohust package/

> make menuconfig

> make package/mentohust/clean

> make package/mentohust/compile

> find bin/ -name 'mentohust*.ipk'

[Back to top](#readme)
