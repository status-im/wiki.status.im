# Messaging




## Chat Protocol Test setup (out of date)

1. Start app in android

2. Build geth:
 ```
 git clone https://github.com/status-im/go-ethereum
 cd go-ethereum
 git checkout develop
 make geth
```
 Alternatively on Mac it can be done by
 ```
 brew tap ethereum/ethereum
brew install ethereum --devel
```
3. Connect to app geth console
 
 ```
 adb forward tcp:8545 tcp:8545
 build/bin/geth attach http://localhost:8545
```
4. Inside console:

 ```
admin.addPeer("enode://e2f28126720452aa82f7d3083e49e6b3945502cb94d9750a15e27ee310eed6991618199f878e5fbc7dfa0e20f0af9554b41f491dc8f1dbae8f0f2d37a3a613aa@139.162.13.89:55555")
```
5. After 10 seconds you should see the peer in:

 `admin.peers`