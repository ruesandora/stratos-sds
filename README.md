<h1 align="center">Stratos SDS </h1>

![image](https://user-images.githubusercontent.com/101149671/181830792-fe8274cc-b1bc-4787-b5cc-2412dcaefb3a.png)

<h1 align="center"> Selamlar arkdaşlar, bugün Stratos SDS ödüllü testnetine katılacağız. </h1>

## Öncelikle sorularınız için kanala katılın: [Stratos Türkiye](https://t.me/StratosTurkish)

## Sistem gereksinimleri:


## root yetkisi:
```
sudo su
```

## root dizinine girelim:
```
cd /root
```

## Sistem güncellemesi:
```
sudo apt update && sudo apt upgrade -y
```

## Kütüphane kurulumu:
```
sudo apt install make clang pkg-config libssl-dev build-essential git jq ncdu bsdmainutils -y < "/dev/null"
```

## Go kurulumu:
```
wget -O go1.18.2.linux-amd64.tar.gz https://golang.org/dl/go1.18.2.linux-amd64.tar.gz 
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.2.linux-amd64.tar.gz && rm go1.18.2.linux-amd64.tar.gz 
echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile 
echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile 
echo 'export GO111MODULE=on' >> $HOME/.bash_profile 
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile 
go version 
```

## source code ile binary dosyayı derliyelim:
```
cd $HOME
git clone https://github.com/stratosnet/sds.git
cd sds
git checkout v0.8.1
make build
cp target/ppd $HOME/bin
```

## binary dosyası oluşturuyoruz:
```
make install
```

## Node dosyası oluşturup bir kaç dokunuş yapıyoruz, burayı iyi dinleyelim:

#### Sırasıyla:

*

```
cd $HOME
mkdir rsnode
cd rsnode
ppd config -w -p
```















