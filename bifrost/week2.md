27.10 Update Node to **v.1.0.2**

# **1. Stop bifrost-node**

docker stop bifrost

# **2. Delete bifrost-node**

docker rm bifrost

# **3. Create container with new version of bifrost-node**

docker run -d -p 30333:30333 -p 9933:9933 -v "/var/lib/bifrost-data:/data" --name "YOUR_NODE_NAME" thebifrost/bifrost-node:latest \
    --base-path /data \
  --chain /specs/bifrost-testnet.json \
  --port 30333 \
  --validator \
  --state-cache-size 0 \
  --runtime-cache-size 64 \
  --telemetry-url "wss://telemetry-connector.testnet.thebifrost.io/submit 0" \
  --name "YOUR_NODE_NAME"
  
  where  "**YOUR_NODE_NAME**" - controller address 
