

![image](https://github.com/user-attachments/assets/242ae371-2dbd-4619-a512-1a8140c36a51)

 * [Topluluk kanalımız](https://t.me/corenodechat)<br>
 * [Topluluk Twitter](https://twitter.com/corenodeHQ)<br>
 * [Discord](https://discord.gg/8ZWgu2pWY4)<br>
 * [Twitter](https://x.com/Covalent_HQ)<br>
 * [covalent Website](https://0g.ai/)<br>
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















