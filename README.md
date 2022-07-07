### Bsc Node Syncing Steps
- Download geth and mainnet using wget from the link below
https://github.com/bnb-chain/bsc/releases/tag/v1.1.8 - Where v1.1.8 is the current latest version (as of 8th March 2022)

- Make the geth_linux downloaded executable
- Unzip the mainnet
- move config.toml and genesis.json to the root folder
- run the command ./geth_linux --datadir ./mainnet init genesis.json to generate genesis
- Download the latest snapshot from https://github.com/bnb-chain/bsc-snapshots by using the command below
wget -q -O - <snapshot URL> | tar -I lz4 -xvf -

`Replacing the <snapshot URL> with "THE_URL_TO_THE_LATEST_GETH"   (quotation marks included)`
- Once downloaded extract it. It will be extracted to the server folder on the downloaded folder.
- Delete the chaindata and triecache data from the datadir folder (mainnet) if it already exists to sync afresh. Use the commands provided below
- Move the chaindata and triecache data of the downloaded snapshot to your datadir (mainnet) using  the commands below

`rm -rf mainnet/geth/chaindata`
`rm -rf mainnet/geth/triecache`
`mv server/data-seed/geth/chaindata mainnet/geth/chaindata`
`mv server/data-seed/geth/triecache mainnet/geth/triecache`

- After moving the snapshot data, start the geth using the command below.
- Remove logs settings from config.toml so that you can see logs in the terminal in real-time.
- To remove the logs settings delete the last part of the config.toml file.
`nano config.toml`
- Start node sync using the command below
./geth_linux --config ./config.toml --datadir ./mainnet --cache 100000 --rpc.allow-unprotected-txs --txlookuplimit 0 --http --maxpeers 100 --ws --syncmode=full --snapshot=false --diffsync

#### Note:
- Geth syncing should be run in a screen session to ensure the process continues even after the ssh session is closed
- If you are using the latest snapshot and notice that the age more than 2 years, most likely you have an eror in you sync setup
- The first place to troubleshoot in such an issue is check that you have initailised the gennesis config correctly. Make sure that the datadir when initialisng the genesis config is correct.
- In case you want to make a change to the the config.toml file or any other config file, just stop the node sync by control + C. After making the change start the node again with the command for starting the node. The change will pick up
- The ip address for the websocket is not include in the config.toml. You need to manually add it



`HAPPY SYNCING`


#### SUMMARY

1. mkdir bscNode 
2. cd bscNode/
3. wget https://github.com/bnb-chain/bsc/releases/download/v1.1.8/geth_linux | tar -I lz4 -xvf - `lastest version as of June 1st 2022 is v1.1.8`
4. wget https://github.com/bnb-chain/bsc/releases/download/v1.1.8/mainnet.zip | tar -I lz4 -xvf -
5. unzip mainnet.zip
6. chmod +x geth_linux  `make geth_linux executable`
7. ./geth_linux --datadir ./mainnet init genesis.json
8. screen -S BscNode `create a screen session to download the node (requires at least 2 TB storage since the snapshot is 1.5 TB)`
9. screen -r BscNode
10. wget -O geth.tar.lz4  "https://tf-dex-prod-public-snapshot.s3-accelerate.amazonaws.com/geth-20220527.tar.lz4?AWSAccessKeyId=AKIAYINE6SBQPUZDDRRO&Signature=l0sbJMq0amrFv03iHLutQ4oljYk%3D&Expires=1656331881" tar -I lz4 xvf geth.tar.lz4 `command to download the snapshot`
11. rm -rf mainnet/geth/chaindata
12. rm -rf mainnet/geth/triecache
13. mv server/data-seed/geth/chaindata mainnet/geth/chaindata
14. mv server/data-seed/geth/triecache mainnet/geth/triecache
15. ./geth_linux --config ./config.toml --datadir ./mainnet --cache 100000 --rpc.allow-unprotected-txs --txlookuplimit 0 --http --maxpeers 100 --ws --syncmode=full --snapshot=false --diffsync `to start the sync`
  
  
  
  
  
  
  
  
  
  
#######################################################################################################################
  
  
  
  
  
 
move config.toml and genesis.json to the root folder
run the command ./geth_linux --datadir ./mainnet init genesis.json to generate genesis
Download the latest snapshot from https://github.com/bnb-chain/bsc-snapshots by using the command below
wget -q -O - <snapshot URL> | tar -I lz4 -xvf -

Replacing the <snapshot URL> with "THE_URL_TO_THE_LATEST_GETH"   (quotation marks included)
Once downloaded extract it. It will be extracted to the server folder on the downloaded folder.
Delete the chaindata and triecache data from the datadir folder (mainnet) if it already exists to sync afresh. Use the commands provided below
Move the chaindata and triecache data of the downloaded snapshot to your datadir (mainnet) using  the commands below

rm -rf mainnet/geth/chaindata
rm -rf mainnet/geth/triecache
mv server/data-seed/geth/chaindata mainnet/geth/chaindata
mv server/data-seed/geth/triecache mainnet/geth/triecache

After moving the snapshot data, start the geth using the command below.
Remove logs settings from config.toml so that you can see logs in the terminal in real-time.
To remove the logs settings delete the last part of the config.toml file.
nano config.toml
Start node sync using the command below
./geth_linux --config ./config.toml --datadir ./mainnet --cache 100000 --rpc.allow-unprotected-txs --txlookuplimit 0 --http --maxpeers 100 --ws --syncmode=full --snapshot=false --diffsync

Note:
Geth syncing should be run in a screen session to ensure the process continues even after the ssh session is closed
If you are using the latest snapshot and notice that the age more than 2 years, most likely you have an eror in you sync setup
The first place to troubleshoot in such an issue is check that you have initailised the gennesis config correctly. Make sure that the datadir when initialisng the genesis config is correct.
In case you want to make a change to the the config.toml file or any other config file, just stop the node sync by control + C. After making the change start the node again with the command for starting the node. The change will pick up
The ip address for the websocket is not include in the config.toml. You need to manually add it



HAPPY SYNCING


Suggested Tags : geth-node, bsc

