# rt-making-wsl-and-windows-work-for-me
WFM :-)

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
