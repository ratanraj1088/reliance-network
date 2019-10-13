# reliance-network
Building a blockchain solution for the 'Asset Tracking System'. This case study is based on the Reliance group of industries and the way the group companies share assets between each other.

# Pre-requisite
Check >> https://hyperledger-fabric.readthedocs.io/en/latest/install.html

Steps:- 
1 . Create a workapces folder 
2. git clone https://github.com/hyperledger/fabric-samples.git 
3. cd fabric-samples
4. ./scripts/bootstrap.sh 1.4.1 1.4.1 0.4.14 
   or
   Fetch bootstrap.sh from fabric repository using
   curl -sS https://raw.githubusercontent.com/hyperledger/fabric/master/scripts/bootstrap.sh -o ./scripts/bootstrap.sh

   Change file mode to executable
   chmod +x ./scripts/bootstrap.sh

   Download binaries and docker images
   ./scripts/bootstrap.sh [version] [ca version] [thirdparty_version]

5 .cd first-network
   ./byfn.sh generate
   
6. ./byfn.sh up 
   or
   sudo ./byfn.sh up
   
7. ./byfn.sh down 
   or
   sudo ./byfn.sh down

# Fabric Configurations steps
1.	Creating certificates for the peer organisations.
.. /bin/cryptogen generate --config crypto-config.yaml
 
   # Genesis Block Transaction

2.	The first artefact was the genesis block, which was generated using the following command:
   ../bin/configtxgen -profile OrdererGenesis -outputBlock ./channel-artifacts/genesis.block
 
   # Channel Configuration Transaction
3.	The next artefact was the channel configuration transaction, which was generated using the following command:
../bin/configtxgen -profile ChannelRelOrgs -outputCreateChannelTx ./channel-artifacts/channel.tx -channelID channelregorgs

 
   # Anchor Peer Transaction

4.	"Generate Reliance Infrastructure  tx" 
 ../bin/configtxgen -profile ChannelRegOrgs -outputAnchorPeersUpdate ./channel-artifacts/InfrastructureAnchor.tx -channelID channelrelorgs -asOrg INFRASTRUCTUREMSP
