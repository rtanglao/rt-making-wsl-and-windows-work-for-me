# rt-making-wsl-and-windows-work-for-me
WFM :-)
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
