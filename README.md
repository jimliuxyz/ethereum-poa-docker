# Ethereum PoA Docker

This project is base on [Capgemini-AIE/ethereum-docker](https://github.com/Capgemini-AIE/ethereum-docker/issues)

# Issue
在AWS EC2上執行時 節點收到rpc命令後極容易crash 原因不明 就連testrpc如此單純的節點都曾經crash過 以下為測試用例 (web3.js under 1.0)
```js
const Web3 = require('web3')

const httpsoc = `http://127.0.0.1:8545`
const provider = new Web3.providers.HttpProvider(httpsoc);

const web3 = new Web3(provider);

console.log(`web3 : ${web3}`)
console.log(`web3.eth.coinbase : ${web3.eth.coinbase}`)

setTimeout(async () => {
  console.log("A")
  let account = await web3.personal.newAccount("");
  console.log("B ", account)
}, 1000);
```

# Issue
netstats相當耗cpu 已將其關閉

# 常用指令
```sh

#啟動docker
docker-compose up

#以ipc方式連入啟動節點
docker exec -it bootstrap geth attach ipc://root/.ethereum/devchain/geth.ipc

```