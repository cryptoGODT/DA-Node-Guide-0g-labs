# DA-Node-Guide-0g-labs
DA Node Guide 🖥️🔐

Each DA signer needs to operate a DA node to perform encoded blob data verification, signing, and storing blob data for further farming and to earn rewards. 🚀

## Hardware Requirements ⚙️

### Minimum Specifications
- **Memory**: 16 GB RAM 💾
- **CPU**: 8 cores 🧠
- **Disk**: 1 TB NVME SSD 💽
- **Bandwidth**: 100 MBps for Download/Upload 🌐

## Installation 🛠️

Follow these steps to get your DA node up and running:

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/0glabs/0g-da-node.git
    ```

2. **Checkout the Specific Version**:
    ```bash
    git checkout tags/v1.0.1 -b v1.0.1
    ```

3. **Build the Project**:
    ```bash
    cargo build --release
    ```

4. **Download Parameters**:
    ```bash
    ./dev_support/download_params.sh
    ```

## Configuration 🛠️🔧

Create a `config.toml` file and configure it with the following values:

```toml
log_level = "info" 📝

data_path = "./db/" 🗄️

# Path to downloaded params folder
encoder_params_dir = "params/" 📂

# gRPC server listen address
grpc_listen_address = "0.0.0.0:34000" 🌐

# Chain ETH RPC endpoint
eth_rpc_endpoint = "https://rpc-testnet.0g.ai" 🌍

# Public gRPC service socket address to register in DA contract
# ip:34000 (keep same port as the gRPC listen address)
# or if you have DNS, fill in your DNS
socket_address = "<public_ip/dns>:34000" 🌟

# Data availability contract to interact with
da_entrance_address = "" 📜

# Deployed block number of DA entrance contract
start_block_number = 0 📈

# Signer BLS private key
signer_bls_private_key = "" 🔑

# Signer ETH account private key
signer_eth_private_key = "" 🔒

# Whether to enable data availability sampling
enable_das = "false" 🚫
```

On the first run of the DA node, it will register the signer information in the DA contract. To generate a BLS private key if you don't have one:

```
cargo run --bin key-gen
```

## Running the Node 🚀

```
./target/release/server --config cargo.toml
```
Your DA node is now up and running! 🎉
