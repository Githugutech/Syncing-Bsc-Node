1. mkdir bscNode 
2. cd bscNode/
3. wget https://github.com/bnb-chain/bsc/releases/download/v1.1.8/geth_linux | tar -I lz4 -xvf -
4. wget https://github.com/bnb-chain/bsc/releases/download/v1.1.8/mainnet.zip | tar -I lz4 -xvf -
5. unzip mainnet.zip
6. chmod +x geth_linux 
7. ./geth_linux --datadir ./mainnet init genesis.json
8. screen -S BscNode
9. screen -r BscNode
10. wget -O geth.tar.lz4  "https://tf-dex-prod-public-snapshot.s3-accelerate.amazonaws.com/geth-20220527.tar.lz4?AWSAccessKeyId=AKIAYINE6SBQPUZDDRRO&Signature=l0sbJMq0amrFv03iHLutQ4oljYk%3D&Expires=1656331881" tar -I lz4 xvf geth.tar.lz4
11. rm -rf mainnet/geth/chaindata
12. rm -rf mainnet/geth/triecache
13. mv server/data-seed/geth/chaindata mainnet/geth/chaindata
14. mv server/data-seed/geth/triecache mainnet/geth/triecache
15. ./geth_linux --config ./config.toml --datadir ./mainnet --cache 100000 --rpc.allow-unprotected-txs --txlookuplimit 0 --http --maxpeers 100 --ws --syncmode=full --snapshot=false --diffsync
