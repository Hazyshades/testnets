# Task 1 Temporarily shut down nodes

*node operators must turn off their node for 4 hours within the designated time frame.*

*Group A: 1 Nov. 2:00 AM - 2:00 PM (UTC)*

*Group B: 3 Nov. 2:00 AM - 2:00 PM (UTC)*

# *1.Set Validator Offline on the polkadot.js.org*

1) visit https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fpublic-01.testnet.thebifrost.io%2Fws#/accounts
2) add account
3) switch from mnemonic to private key
4) delete random private key and insert the one you have in metamask, startng with 0x
5) finish importing your controller account
after that 
6) Developer-extrinsics-bfcStaking-goOffline()" extrinsic and submit tx

# **2. Stop bifrost-node**

docker stop **bifrost** 
*here **bifrost** is "YOUR_NODE_NAME"*

# **3.  Wait a 4 hours**

# **4. Set Validator Online on the polkadot.js.org** 

1) visit https://polkadot.js.org/apps/?rpc=wss%3A%2F%2Fpublic-01.testnet.thebifrost.io%2Fws#/accounts
2) Developer-extrinsics-bfcStaking-goOffline()" extrinsic and submit tx

# **5. Return bifrost-node to live**

docker start **bifrost**

