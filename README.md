<h1 align="center">Stratos SDS </h1>

![image](https://user-images.githubusercontent.com/101149671/181830792-fe8274cc-b1bc-4787-b5cc-2412dcaefb3a.png)

<h1 align="center"> Selamlar arkdaşlar, bugün Stratos SDS ödüllü testnetine katılacağız. </h1>

## Öncelikle sorularınız için kanala katılın: [Stratos Türkiye](https://t.me/StratosTurkish)

<h1 align="center"> ÖNEMLİ! Arkadaşlar kolay bir testnet olmayacak, kurmanız belki 2 belki 3 günü olacak, çok büyük bir ricamdır sabırlı olmanız, bu flood vs. silindi tekrar yazdım, ricamdır sabırlı olmanız ve stratos türkiye grubunun sabitli mesajlarını ara ara bakmanız, tek isteğim :heart: </h1>

# SDS kurmak için validator oluşturmanız gerekmez ve stratos validatoru ile aynı yere kurabilirsiniz.

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

#### Sırasıyla (elektirikler gitti ve görsel alamadım bu kısmı kusura bakmayın):

* 1- Şifreyi girelim
* 2- Şifreyi tekrar girelim
* 3- Cüzdan adı
* 4- Şifre tekrar
* 5- bip39 sorusunu sadece enter diyelim (eski stratos cüzdanınız varsa 12 kelımesını girebilirsiniz)
* 6- Tekrar enter
* 7- Son olara Y (yes) diyerek bitiriyoruz.

```
cd $HOME
mkdir rsnode
cd rsnode
ppd config -w -p
```

## Confingin içine girelim ve sırayla görsellerle altta anlatıyorum:
```
nano $HOME/rsnode/configs/config.toml
```

### network_adres kısmına sunucumuzun IP numarasını girelim:

![image](https://user-images.githubusercontent.com/101149671/181833410-d4cb6c93-f20b-459b-a99c-bd393e7969ce.png)

### Cüzdan adreslerini ve şifremizi not edip saklayalım:

![image](https://user-images.githubusercontent.com/101149671/181833561-f32eea30-6a7d-42ff-9c4c-8571e4211789.png)

### chain id kısmı tropos-4 olacak değilse düzeltirsiniz:

![image](https://user-images.githubusercontent.com/101149671/181833686-feadd6fa-913d-4dcc-b4ed-fd3a1c34ef50.png)

### Stratos chain url'yi değiştirelim:

* https://rest-tropos.thestratos.org:443

![image](https://user-images.githubusercontent.com/101149671/181833790-d29be4a0-9bc6-4e7b-a282-03ceb7f3ad07.png)

### Version kısmı görselde ki gibi olacak, değilse değişirsiniz zaten:

![image](https://user-images.githubusercontent.com/101149671/181833922-8f7c212b-1d7e-4a1d-bbdf-51e97f46f725.png)

### Son olarak [[sp_list]] 'inizde sadece 1 tane liste olacak, benim altta verdiklerimi ekleyin görselde ki gibi olacak.

![image](https://user-images.githubusercontent.com/101149671/181834026-2823e527-a5d9-4e61-b69f-5fc8ffb30816.png)

```
[[sp_list]]
p2p_address = 'stsds1mr668mxu0lyfysypq88sffurm5skwjvjgxu2xt'
p2p_public_key = 'stsdspub1zcjduepq4v8yu6nzem787nfnwvzrfvpc5f7thktsqjts6xp4cy4a2j4rgm7sgdy4zy'
network_address = '35.73.160.68:8888'
[[sp_list]]
p2p_address = 'stsds1ftcvm2h9rjtzlwauxmr67hd5r4hpxqucjawpz6'
p2p_public_key = 'tsdspub1zcjduepqq9rk5zwkzfnnszt5tqg524meeqd9zts0jrjtqk2ly2swm5phlc2qtrcgys'
network_address = '46.51.251.196:8888'
[[sp_list]]
p2p_address = 'stsds12uufhp4wunhy2n8y5p07xsvy9htnp6zjr40tuw'
p2p_public_key = 'stsdspub1zcjduepqkst98p2642fv8eh8297ppx7xuzu7qjz67s9hjjhxjxs834md7e0s5rm3lf'
network_address = '18.130.202.53:8888'
[[sp_list]]
p2p_address = 'stsds1wy6xupax33qksaguga60wcmxpk6uetxt3h5e3e'
p2p_public_key = 'stsdspub1zcjduepqyyfl7ljwc68jh2kuaqmy84hawfkak4fl2sjlpf8t3dd00ed2eqeqlm65ar'
network_address = '35.74.33.155:8888'
[[sp_list]]
p2p_address = 'stsds1nds6cwl67pp7w4sa5ng5c4a5af9hsjknpcymxn'
p2p_public_key = 'stsdspub1zcjduepq6mz8w7dygzrsarhh76tnpz0hkqdq44u7usvtnt2qd9qgp8hs8wssl6ye0g'
network_address = '52.13.28.64:8888'
[[sp_list]]
p2p_address = 'stsds1403qtm2t7xscav9vd3vhu0anfh9cg2dl6zx2wg'
p2p_public_key = 'stsdspub1zcjduepqzarvtl2ulqzw3t42dcxeryvlj6yf80jjchvsr3s8ljsn7c25y3hq2fv5qv'
network_address = '3.9.152.251:8888'
[[sp_list]]
p2p_address = 'stsds1hv3qmnujlrug00frk86zxr0q23rnqcaquh62j2'
p2p_public_key = 'stsdspub1zcjduepqj69eeq07yfdgu4cdlupvga897zjqjakuru0qar5na7as4kjr7jgs0k7aln'
network_address = '18.223.175.117:8888'
```

### Son olarak görselde ki gibi bir görünüm alacaksınız ve ctrl + x 'e basıp y diyoruz ve enterliyoruz.

![image](https://user-images.githubusercontent.com/101149671/181834279-98a286c3-6ac8-4e1d-831d-ca5a8555a656.png)

## Faucetten token alıyoruz, komutu terminale girelim:

* CÜZDANADRESİ kısmını cüzdan adresinizi girin
* Cüzdan adresimizi az önce not almıştık p2p adres değil wallet adres yazan yer.
* tokenleri kontrol etmek isterseniz: [explorer linki](https://big-dipper-tropos.thestratos.org/)

```
curl --header "Content-Type: application/json" --request POST --data '{"denom":"ustos","address":"CÜZDANADRESİ"} ' https://faucet-tropos.thestratos.org/credit
```

### tmux kurulumu:

* y/n onayı çıkınca y diyelim.

```
apt-get install tmux
```

### oturum açalım:
```
tmux new-session -s sds
```

### SDS nodu başlatalım:

* Burayıda resim alamadım, burada en sonda ERROR yazacak ve sonunda "please register at first" yazacak, yazana kadar bekleyelim.

* Çıktıyı aldıktan sonra ctrl+b bası kısa bir süre sonra d'ye basalım, aynı anda basmayın çıkış yapmaz.

```
cd ~/rsnode
ppd start
```

### screeni yüklüyoruz:
```
apt-get install screen
```

### terminal adında screen oluşturuyoruz:
```
screen -S terminal
```

### resource node ile etkileşim kurabilmek için ek terminal açalım:

* buradan sonra komutları girerken ">" işaretlerinin üzerine yazıyoruz.

```
cd ~/rsnode
ppd terminal
```

![image](https://user-images.githubusercontent.com/101149671/181835946-cc4227ed-7b10-4875-8e2c-61f34d786616.png)

### registerpeer ekleyelim:

* PP successfully çıktısı almalıyız

```
registerpeer
```

### activate işlemi yapalım:

* Bu komutu girdikten sonra uzun bir süre (veya kısa) bekleyip true çıktısı almalısınız

```
activate 10000000000 10000 1000000
```

### Node durumuna bakaım:

* Sizde Activation: Active | Mining: ONLINE | Initial tier: 1 | Ongoing tier: 1 | Weight score: 5000 yazacak.

```
status
```

![image](https://user-images.githubusercontent.com/101149671/181836273-41579d54-acc6-4652-af2e-7226f09ee8d8.png)


### Otomatik dosya oluşturup yüklüyoruz:

* Ozon alıyoruz:

```
prepay 1000000000 10000 600000
```

### Bakalım ozonlar gelmiş mi:

* Cüzdan adresi kısmına cüzdanınız girin

* Miktar sizde farklı olacaktır (ben önceden kurdum ama flood silindi)

* Bunu yaptıktan sonra ctrl+a basıp d diyelim ve çıkalım

```
getoz cüzdanadresi
```

![image](https://user-images.githubusercontent.com/101149671/181838423-334acdb7-4dc4-4cec-8a5e-301179024b4d.png)

### upload isimli bir screen açalım:
```
screen -S upload
```

### Aynı sekılde klasor acalım:
```
mkdir -p ~/upload
```

### upload.sh'a girelim:
```
nano $HOME/rsnode/upload.sh
```

### script komutlarımızı yapıştıralım:

* Not girdiğimiz dosyanın içinde ki tüm kodları silelim ve altta ki komutu girelim.
* ctrl+x diyip Y ile kaydedelim sonra.

```
#!/bin/bash
while true;
do /usr/bin/head -c 25M /dev/urandom > "$HOME/upload/test-$(date '+%Y%m%d%H%M')" ; ppd terminal exec put "$HOME/upload/test-$(date '+%Y%m%d%H%M')";
sleep 900;
/usr/bin/rm -rf "$HOME/upload/test*";
sleep 1;
done
```

![image](https://user-images.githubusercontent.com/101149671/181839129-11e77ec4-775c-4f51-9fa3-e4954b5e9e78.png)

### Son olarak yetkiyi veriyoruz ve bitiriyoruz:
```
cd $HOME/rsnode
chmod +x upload.sh 
./upload.sh
```

![image](https://user-images.githubusercontent.com/101149671/181839334-f02f3f93-3b7c-4ab3-afc7-a84091b3df9a.png)


### Kazandığımız ödülleri (hemen yansımaz) kontrol etmek içim:

* st1jmxxx.. diye başlayan cüzdana kendi cüzdan adresinizi girip google'da aratın, hemen yansımaz, 1-2 gün sonra bakın.

```
https://rest-tropos.thestratos.org/pot/rewards/wallet/st1jmxxzgy6jevnd3gpejyqr4mvrfj8hqkh2p9yen
```

# Sorun yaşarsanız lütfen grupta [grup linki](https://t.me/StratosTurkish) arama kısmını kullanın ricamdır, çok yoğun ve yorgun dönemlerdeyim/dönemlerdeyiz.

![image](https://user-images.githubusercontent.com/101149671/181839812-e79667ee-d61e-4cd4-af05-8412fce5d97d.png)

# Hesaplar:

[<img src="https://cdn-icons-png.flaticon.com/512/733/733579.png" width="16px"> Twitter   ](https://twitter.com/Ruesandora0) 

[<img src="https://cdn-icons-png.flaticon.com/512/1336/1336494.png" width="16px"> Forum   ](https://forum.rues.info/index.php)

[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Announcement   ](https://t.me/RuesAnnouncement)

[<img src="https://cdn-icons-png.flaticon.com/512/2111/2111646.png" width="16px"> Telegram Chat   ](https://t.me/+-l6GpqiNOxFiMTVk)

[Discord](https://discord.gg/ruescommunity)
