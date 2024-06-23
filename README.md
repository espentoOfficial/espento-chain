## Hyperledger Besu: Step-by-Step Guide to Setting Up a Node

### Prerequisites

1. **Java Development Kit (JDK)**: Ensure you have JDK 17 or higher installed.
2. **Hardware Requirements**: At least 8 GB RAM and 100 GB free disk space.
3. **Operating System**: Linux, macOS, or Windows.

### Step 1: Download Hyperledger Besu Binary

1. Go to the [Hyperledger Besu releases page](https://github.com/hyperledger/besu/releases/tag/23.1.0).
2. Download the latest binary for your operating system:
   - **Linux/macOS**: `besu-<version>-linux.tar.gz`

### Step 2: Install Hyperledger Besu

#### For Linux/macOS:

1. Open a terminal.
2. Extract the downloaded tarball:
   ```bash
   tar -xzf besu-<version>-linux.tar.gz
   ```
3. Move the extracted files to your desired directory, for example:
   ```bash
   sudo mv besu-<version> /usr/local/bin/besu
   ```
4. Add `besu` to your PATH by adding the following line to your `~/.bashrc` or `~/.zshrc` file:
   ```bash
   export PATH=$PATH:/usr/local/bin/besu/bin
   ```
5. Apply the changes:
   ```bash
   source ~/.bashrc
   ```

### Step 3: Configure Hyperledger Besu

1. Edit provided configuration file `config.toml`.

### Step 4: Start Hyperledger Besu Node

1. Open a terminal (or command prompt on Windows).
2. Navigate to the directory containing the `config.toml` file.
3. Start the node:
   ```bash
   besu --config-file=config.toml
   ```

### Step 5: Verify Node Status

1. Open a new terminal or command prompt.
2. Use `curl` to check if the node is running correctly:
   ```bash
   curl -X POST --data '{"jsonrpc":"2.0","method":"net_version","params":[],"id":1}' http://localhost:8545
   ```
3. You should receive a JSON response indicating the network ID.

### Step 6: Connect and Sync with the Network

1. **Syncing with Mainnet**: By default, the node will start syncing with the Ethereum mainnet.
2. **Sync Progress**: Monitor the log output to see the sync progress. The node will download blocks and state until it catches up with the current chain head.

### Step 7: Use JSON-RPC API to Interact with the Node

1. **Send Requests**: Use tools like `curl`, Postman, or any Ethereum-compatible client to send JSON-RPC requests to your Besu node.
2. **Example Request**: Fetch the latest block number:
   ```bash
   curl -X POST --data '{"jsonrpc":"2.0","method":"eth_blockNumber","params":[],"id":1}' http://localhost:8545
   ```
3. **Explore APIs**: Refer to the [Hyperledger Besu JSON-RPC API documentation](https://besu.hyperledger.org/en/stable/Reference/API-Methods/) for more methods you can use.

### Step 8: Additional Configuration (Optional)

1. **Enable WebSocket**:
   ```toml
   rpc-ws-enabled = true
   rpc-ws-host = "0.0.0.0"
   rpc-ws-port = 8546
   rpc-ws-api = ["ETH", "NET", "WEB3"]
   ```

2. **Enable Metrics**:
   ```toml
   metrics-enabled = true
   metrics-host = "0.0.0.0"
   metrics-port = 9545
   ```

### Conclusion

You've successfully set up a Hyperledger Besu node! You can now interact with the Ethereum network using JSON-RPC APIs. Explore more configuration options and features in the [official documentation](https://besu.hyperledger.org/).

For any issues or further assistance, refer to the [Hyperledger Besu documentation](https://besu.hyperledger.org/) and community forums. Happy coding!
