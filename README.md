# Storage-node

<img width="2048" height="713" alt="image" src="https://github.com/user-attachments/assets/d0ac8a92-4d29-44e0-b9ba-9b5af36aecfd" />

# Upgrade to new release {v1.1.0}

1. Stop the storage node
```
sudo systemctl stop zgs
```

2. Change Repo , Fetch the latest tags and switch to the new release
```
cd ~/0g-storage-node
```
```
git reset --hard
git clean -fd
```
```
git fetch --all
git checkout v1.1.0
```
```
git submodule update --init --recursive
```

3. Build the new release
```
sudo apt-get install protobuf-compiler
```
```
cargo build --release
```

4. Set config
```
rm -rf $HOME/0g-storage-node/run/config.toml
curl -o $HOME/0g-storage-node/run/config.toml https://vault.astrostake.xyz/testnet/0g-labs/config-v3.toml
```
- Edit miner key & RPC 
<img width="831" height="299" alt="image" src="https://github.com/user-attachments/assets/eda1f4bc-a30b-4202-af5c-289d7d47e014" />

- RPC
```
https://0g-evm.maouam.nodelab.my.id/
```

5. Start your Node
```
sudo systemctl start zgs
```


## Check logs:
```
tail -f ~/0g-storage-node/run/log/zgs.log.$(TZ=UTC date +%Y-%m-%d)
source <(curl -s https://raw.githubusercontent.com/astrostake/0G-Labs-script/refs/heads/main/storage-node/check_block.sh)
```


Done ma bro!


















