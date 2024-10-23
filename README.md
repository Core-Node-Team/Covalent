

![image](https://github.com/user-attachments/assets/242ae371-2dbd-4619-a512-1a8140c36a51)

 * [Topluluk kanalımız](https://t.me/corenodechat)<br>
 * [Topluluk Twitter](https://twitter.com/corenodeHQ)<br>
 * [Discord](https://discord.gg/8ZWgu2pWY4)<br>
 * [Twitter](https://x.com/Covalent_HQ)<br>
 * [covalent Website](https://www.covalenthq.com/tr/)<br>
 * [covalent gitbook/docs](https://www.covalenthq.com/docs/nodes/ewm-light-client/run-ewm-lc)<br>
 * [covalent Telegram](https://t.me/CovalentHQ)<br>
 * [Staking Page](https://www.covalenthq.com/staking/)<br>

### Waitlist Form

https://forms.gle/sS1RDAgUwju7UQV19


## 💻 Sistem Gereksinimleri
| Bileşenler | Minimum Gereksinimler | 
| ------------ | ------------ |
| CPU |	2 |
| RAM	| 4 GB |
| Storage	| 50 GB SSD |

### 🚧Gerekli kurulumlar
```
sudo apt update && sudo apt upgrade -y
sudo apt install curl git wget htop tmux build-essential jq make pkg-config libssl-dev lz4 gcc unzip -y
```

### Go kurulumu
```
wget https://go.dev/dl/go1.22.3.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.22.3.linux-amd64.tar.gz

echo "" >> ~/.bashrc
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export GOROOT=/usr/local/go' >> ~/.bashrc
echo 'export GOBIN=$GOPATH/bin' >> ~/.bashrc
echo 'export PATH=$PATH:/usr/local/go/bin:$GOBIN' >> ~/.bashrc

source ~/.bashrc
```

### Docker kurulumu ve gereklilikler.

```
sudo apt-get update
```
```
sudo apt-get install ca-certificates curl gnupg
```
```
sudo install -m 0755 -d /etc/apt/keyrings
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt-get update
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
### IPFS kurulumu
```
wget https://dist.ipfs.tech/kubo/v0.30.0/kubo_v0.30.0_linux-amd64.tar.gz
tar -xvzf kubo_v0.30.0_linux-amd64.tar.gz
```
```
cd kubo
sudo bash install.sh
```
```
ipfs --version
```
### Covalent reposunu çekelim ve build edelim
```
cd
git clone https://github.com/covalenthq/ewm-das
cd ewm-das
```
#### Build
NOT: uzun sürüyor.
```
docker build -t covalent/light-client -f Dockerfile.lc .
```
### Çalıştıralım
NOT: private key yazıyoruz mm dan bir burner cuzdan olusturun yada varsa kullanın.
```
docker run -d --restart always --name light-client -e PRIVATE_KEY="HA-BURE private-yazıyoruz tırnak necmi kalıyor" covalent/light-client
```
### LOG kontrol
```
docker logs -f light-client
```


![image](https://github.com/user-attachments/assets/93c5c396-d132-4eb8-802b-79d4d42085c4)





### işlem sonu

- mailde bize bir form veriyor register formu ona ilk mainnet için nft alacağımız cüzdanı daha sonrada nodu kurarken girdiğim private burner cüzdanın adresini yaızyoruz ve gönderiyoruz. discorda giriyoruz. başka bişi suan için yok maili translate ile çevirip okuyun ve discorda sorun.


### Dockersız kurulum YAPIM AŞAMASINDA GÖRMEZDEN GELİN

git clone https://github.com/covalenthq/ewm-das
cd ewm-das
make deps
make

wget https://github.com/covalenthq/ewm-das/releases/download/v0.11.0-rc1/das-ubuntu-v0.11.0-rc1.tar.gz && tar -xf das-ubuntu-v0.11.0-rc1.tar.gz

./bin/light-client --rpc-url ws://coordinator.das.test.covalentnetwork.org/rpc --collect-url https://us-central1-covalent-network-team-sandbox.cloudfunctions.net/ewm-das-collector --private-key ${PRIVATE_KEY}


tail -n 1000 -f $HOME/.covalent/light-client.log


### Güncelleme
NOT: private key yaz.
```
cd $HOME/ewm-das && git config --global --add safe.directory /root/ewm-das && git stash && git pull origin main && git stash pop && git fetch --all && git checkout main && git pull origin main && git tag && git checkout v0.13.0 && git switch -c v0.13.0 && docker build -t covalent/light-client -f Dockerfile.lc . && docker stop light-client && docker rm light-client && docker run -d --restart always --name light-client -e PRIVATE_KEY="private-yaz" covalent/light-client && docker logs -f light-client
```







