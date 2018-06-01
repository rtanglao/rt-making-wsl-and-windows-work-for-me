# rt-making-wsl-and-windows-work-for-me
WFM :-)
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
./configure
make
sudo make install
ruby -v
sudo apt-get install zlib1g-dev
 ```
