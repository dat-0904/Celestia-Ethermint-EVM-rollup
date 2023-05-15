# Celestia-Ethermint-EVM-rollup

# Celestia-Ethermint-EVM-rollup	# Celestia-Ethermint-EVM-rollup

Recommended configuration:

    Ram: 8 GB RAM
    Chip: 4 Core
    Ổ cứng: 250 GB SSD Storage
    Băng thông: 1 Gbps for Download/100 Mbps for Upload
Using Ubuntu 20.04 OS Install Golang 1.19 or later

1/ Install Roollkit:

    git clone https://github.com/celestiaorg/ethermint.git
    cd ethermint
    make install

2/ Run a copy of Celestia light-node

    https://docs.celestia.org/nodes/light-node/

    bash init.sh

3/ Add information and block height:

    NAMESPACE_ID=$(echo $RANDOM | md5sum | head -c 16; echo;)
    DA_BLOCK_HEIGHT=$(curl https://rpc-blockspacerace.pops.one/block | jq -r '.result.block.header.height')
Faucet Mocha token to the wallet running the node, then run the command:

    ethermintd start --rollkit.aggregator true --rollkit.da_layer celestia --rollkit.da_config='{"base_url":"http://localhost:26659","timeout":60000000000,"gas_limit":6000000,"fee":6000}' --rollkit.namespace_id $NAMESPACE_ID --rollkit.da_start_height $DA_BLOCK_HEIGHT 

4/ Update...
