# rt-making-wsl-and-windows-work-for-me
WFM :-)

# 29-30May2019 ARM64 Windows 10 Laptop Lenovo Yoga C630
## 29May2019 installing firefox arm64 windows

* got it from https://ftp.mozilla.org/pub/firefox/nightly/latest-mozilla-central/
    * url changes every day but the one for firefox 69 nightly is : 
        * https://ftp.mozilla.org/pub/firefox/nightly/latest-mozilla-central/firefox-69.0a1.en-US.win64-aarch64.installer.exe
    
# 15april2019 pip

```
mkdir PIP
cd PIP
sudo  apt-get install python3-venv
python3 -m venv .
source bin/activate
pip3 install pandas
 ```

# 31march2019 

```bash
 install.packages('jpeg')
```

# 10february2019 install miller for concatenating files

```bash
sudo apt-get install miller
```

# 09February2019 install ruby 2.6.1 to get readline support

```bash
sudo apt-get update
sudo apt install -y libreadline-dev
sudo apt-get install build-essential
cd
wget http://ftp.ruby-lang.org/pub/ruby/2.6/ruby-2.6.1.tar.gz
tar -xzvf ruby-2.6.1.tar.gz
cd ruby-2.6.1/
sudo apt-get install zlib1g-dev
sudo apt-get update -y && sudo apt-get upgrade -y
sudo apt-get install libssl-dev
./configure
make
sudo make install
ruby -v
sudo gem update --system
sudo gem install jekyll bundler
sudo gem install redcarpet
```

# 20January2019 install wsl-open to replace open, works for PNGs

```bash
sudo npm install -g wsl-open
open blah.png # launches photos on the windows side after copying the file to windows
```

# 08January2019 how to start up R Studio server after every reboot on WSL

```bash
sudo rstudio-server start
```

# 04January2019 install libsasl2-dev to be able to install mongolite package

```bash
sudo apt-get install libsasl2-dev
```
# 02January2019 making timezones work

```bash
sudo dpkg-reconfigure tzdata
```

# 02January2019 making firefox work

* fix fonts, make dbus work
```bash
sudo apt-get install dbus-x11
sudo service dbus start
sudo apt-get install ubuntu-desktop
```

* in firefox turn off multi-process from cor-e, UNSUPPORTED!!! ( from https://support.mozilla.org/nl/questions/1167673 )
```
You can disable multi-process windows in Firefox by setting these prefs to false on the about:config page.

   
   browser.tabs.remote.autostart = false
   
   browser.tabs.remote.autostart.2 = false 
```


# 01January2019 installing R
* from: https://linuxize.com/post/how-to-install-r-on-ubuntu-18-04/

```bash
sudo vi /etc/apt/sources.list
# and add the following line to the end:
# deb https://cloud.r-project.org/bin/linux/ubuntu bionic-cran35/
sudo apt install apt-transport-https software-properties-common
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 51716619E084DAB9 
# above line is from https://askubuntu.com/questions/610449/w-gpg-error-the-following-signatures-couldnt-be-verified-because-the-public-k
sudo apt-get update
```

* and then install R
from: http://johnmuschelli.com/neuroc/windows_wsl/index.html
```bash
sudo apt-get install r-base
```

* and then install openssh as per https://virtualizationreview.com/articles/2017/02/08/graphical-programs-on-windows-subsystem-on-linux.aspx

```bash
sudo apt-get remove  openssh-server
sudo apt-get install  openssh-server
```

<blockquote>
 A few other parameters will also need to be changed in the OpenSSH configuration file. The file -- /etc/ssh/sshd_config -- will need to be edited to add/change the following:

Change - PermitRootLogin no

Add - AllowUsers yourusername

Change - PasswordAuthentication yes

Add - UsePrivilegeSeparation no

Change - ListenAddress 0.0.0.0

Change - Port 2200

After these changes have been made, the SSH service will need to be restarted:

\# sudo service ssh --full-restart
</blockquote>

* install x11 programs just like 1985 :-)

```bash
sudo apt-get install x11-apps
```

* install firefox just for fun :-) not sure how good it will work !

```bash
sudo apt-get install firefox
/usr/bin/x-www-browser # to invoke firefox on X!
```

* install rstudio and gdebi

```bash
export RSTUDIO_VERSION=$(wget --no-check-certificate -qO- https://s3.amazonaws.com/rstudio-server/current.ver)
echo "VERSION ${RSTUDIO_VERSION}"
sudo wget -q http://download2.rstudio.org/rstudio-server-${RSTUDIO_VERSION}-amd64.deb
sudo gdebi --non-interactive rstudio-server-${RSTUDIO_VERSION}-amd64.deb
sudo rm rstudio-server-*-amd64.deb 
# run rstudio on the windows side!
http://localhost:8787 # https://localhost:8787 didn't work!
```

* install r dev tools pre requisites

```bash
sudo apt-get update -qq -y
sudo apt-get install -y libgit2-dev 
sudo apt-get install -y libcurl4-openssl-dev libssl-dev
sudo apt-get install -y zlib1g-dev libssh2-1-dev libpq-dev libxml2-dev 
sudo apt-get install -y libhdf5
```
# 01January2019 can't make sublime markdown theme's work 

```
Error loading syntax file "Packages/Markdown/Markdown.sublime-syntax": 
Unable to read Packages/Markdown/Markdown.sublime-syntax
```

# 28December2018 let's try installing X windows and sublime

* from [Windows Subsystem for Linux - Editor (GUI) Setup](https://www.lambrospetrou.com/articles/windows-linux-subsystem-editor-setup/) 
  * https://sourceforge.net/projects/xming/

* and then:

```bash
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
sudo apt-get update && sudo apt-get install sublime-text
```

* but then gtk errors so i followed [Unable to start sublime text](https://askubuntu.com/questions/228169/unable-to-start-sublime-text)
```bash
sudo apt-get install libgtk2.0
```
* and then to make sublime package control work as per [https://packagecontrol.io/installation](https://packagecontrol.io/installation):

```bash
mkdir ~/.config/sublime-text-3/Installed Packages
```
* and then install fonts

```bash
git clone --depth 1 --branch release https://github.com/adobe-fonts/source-code-pro.git ~/.fonts/adobe-fonts/source-code-pro
fc-cache -f -v ~/.fonts/adobe-fonts/source-code-pro
```

# 20december2018 installing zsh

```bash
sudo apt-get install zsh
sudo apt-get install xtitle
zsh
# picked 2 as in:
# (2)  Populate your ~/.zshrc with the configuration recommended
#     by the system administrator and exit (you will need to edit
#     the file by hand, if so desired).
# added zsh to the end of ~/.bashrc
```

# 17december2018 install mongodb 4.0.4

* https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/#install-the-mongodb-packages

```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```

# 17december2018 install node and surge

```bash
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -
sudo apt-get install -y nodejs
sudo npm install --global surge
```
# 17december2018 add exclusion for Windows Defender

* https://medium.com/@leandrw/speeding-up-wsl-i-o-up-than-5x-fast-saving-a-lot-of-battery-life-cpu-usage-c3537dd03c74


# 17december2018 after re-install of Windows 10, install ruby 2.5.3

```bash
sudo apt-get update
sudo apt-get install build-essential
cd
wget http://ftp.ruby-lang.org/pub/ruby/2.5/ruby-2.5.3.tar.gz
tar -xzvf ruby-2.5.3.tar.gz
cd ruby-2.5.3/
sudo apt-get install zlib1g-dev
sudo apt-get update -y && sudo apt-get upgrade -y
sudo apt-get install libssl-dev
./configure
make
sudo make install
ruby -v
sudo gem update --system
sudo gem install jekyll bundler
sudo gem install redcarpet
```


# 12november 2018 add imagemagick
```bash
sudo apt-get update
sudo apt-get install imagemagick
```

# 04November2018 added zsh
* installed zsh with apt-get
* installed xtitle with apt-get
* added zsh to the end of ~/.bashrc
* the above enabled ```xtitle blah``` ! xtitle didn't work in bash i.e. it didn't set the tite of the window in the Windows 10 launchbar
* to get rid of ```_z_precmd:1: nice(5) failed: operation not permitted```:
  * added ```setopt nobgnice``` to ```.zshrc```

# 06October2018 update to git 2.19.1

* because of this security advisory https://marc.info/?l=git&m=153875888916397&w=2

```bash
sudo apt-get update
sudo apt-get install git
```

# 07September2018 libcurl  and curl.h

```bash
sudo apt-get install libcurl4-openssl-dev
```

# 30June2018-7z-unzip
* used 7-Zip to un-compress emacs
# 30June2018-emacs
* https://github.com/m-parashar/emax64/releases/
** emax64-pdumper-bin-20180619.7z
** installed into ~/Documents
# 28June2018 Mongodb
see https://gist.github.com/Mikeysax/cc86c30903727c556bcce960f7e4d59b

```bash
    Open a Windows PowerShell and type wsl.
    Type cd ~ to go to the root of the Ubuntu File System.
    Paste sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5

    This will "... import the MongoDB public GPG Key" so we can use the official MongoDB supported pkg in apt.

    Paste echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.6.list

    This will add the deb to your sources list.
    Note that you must be on Ubuntu Xenial. When Zesty gets LTS we will update this doc.

    Reload your local pkg database by typing sudo apt-get update.
    Run the install command by pasting sudo apt-get install -y mongodb-org.

    This will install the most stable version of mongod, 3.6 at time of writing. If you want to install a different version please refer to the link above.
```

# 04June2018 Hugo

```bash
wget -O /tmp/hugo_0.41_Linux-64bit.deb https://github.com/spf13/hugo/releases/download/v0.41/hugo_0.41_Linux-64bit.deb
sudo apt install /tmp/hugo_0.41_Linux-64bit.deb
hugo version
Hugo Static Site Generator v0.41 linux/amd64 BuildDate: 2018-05-25T16:57:20Z
cd themes
git clone https://github.com/halogenica/beautifulhugo.git beautifulhugo
```

# 02June2018
* from [How to setup github credential caching on Windows Linux subsystem](http://rolandtanglao.com/2018/03/02/p2-how-to-setup-github-credential-caching/)
```bash
git config --global credential.helper cache
```
* in  ~/.gitconfig but just in case here's the line to add

```
[credential]
        helper = cache --timeout=144000
```

# 01June2018

from: https://docs.microsoft.com/en-us/windows/wsl/install-win10: install linux (ubuntu in my case)

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

install stuff so i can compile ruby:

```bash
sudo apt-get update
sudo apt-get install build-essential
cd
wget http://ftp.ruby-lang.org/pub/ruby/2.5/ruby-2.5.1.tar.gz
tar -xzvf ruby-2.5.1.tar.gz
cd ruby-2.5.1/
sudo apt-get install zlib1g-dev
sudo apt-get update -y && sudo apt-get upgrade -y
sudo apt-get install libssl-dev
./configure
make
sudo make install
ruby -v
sudo gem update --system
sudo gem install jekyll bundler
sudo gem install redcarpet
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs 
sudo npm install --global surge
sudo add-apt-repository ppa:git-core/ppa
sudo apt update; sudo apt install git
```
