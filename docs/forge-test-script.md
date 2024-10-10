### ERC20 token
1) Install the latest version
```
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

2) Create a new project:
```
forge init erc20-token
cd erc20-token
```
3) Install OpenZeppelin contracts:
```
forge install OpenZeppelin/openzeppelin-contracts
```
4) In the `src` directory, create a new file called `MyToken.sol` and add the following code for the ERC20 contract:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    constructor(uint256 initialSupply) ERC20("MyToken", "MTK") {
        _mint(msg.sender, initialSupply * (10 ** decimals()));
    }
}
```
5) To deploy the contract, create a script under the script/ folder, e.g., `DeployToken.s.sol`:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "forge-std/Script.sol";
import "../src/MyToken.sol";

contract DeployTokenScript is Script {
    function run() external {
        uint256 deployerPrivateKey = vm.envUint("PRIVATE_KEY");
        uint256 initialSupply = 1000000; // 1 million tokens

        vm.startBroadcast(deployerPrivateKey);

        new MyToken(initialSupply);

        vm.stopBroadcast();
    }
}
```
6) Configure Foundry
Edit the `foundry.toml` file to specify the Solidity version:
```
[profile.default]
src = 'src'
out = 'out'
libs = ['lib']
solc_version = '0.8.20'

[default]
rpc_url = 'https://api.harmony.one'
```

7) Set Environment Variables, create .env file under `erc20-token` folder:
```
0x<PRIVATE_KEY>
```

8) Deploy the contract:
```
forge script script/DeployToken.s.sol --broadcast --rpc-url https://api.harmony.one --legacy
```

sample output:
```
[⠊] Compiling...
No files changed, compilation skipped
Script ran successfully.

## Setting up 1 EVM.

==========================

Chain 1666600000

Estimated gas price: 100 gwei

Estimated total gas used for script: 726685

Estimated amount required: 0.0726685 ETH

==========================
⠁ Sequence #1 on 1666600000 | Waiting for pending transactions
    ⠠ [Pending] 0x0bc8a3a511762a5128f1d458956888cea7721f1a432caa60348b71c5a50011a9
```

<img width="1326" alt="Screenshot 2024-10-10 at 7 46 25 PM" src="https://github.com/user-attachments/assets/bec8aaea-d7ee-41e7-bf30-38e339a9f3f3">


9) Do not need to wait for receipt, open the Explorer and find transaction hash from output above:

https://explorer.harmony.one/tx/0x5fd00fe210e09484d9b0f2011fe438e124887396ac0aa0a2b6f6ded3e1a74c39

<img width="878" alt="Screenshot 2024-10-10 at 7 45 39 PM" src="https://github.com/user-attachments/assets/d8fc2a0a-2d98-44c3-a6d0-5881cf90eeb7">

Contract address: 0xe9df1e36b7188edaf91b208b9ea6508b2902f517

10) Check the deployed contract:
```
cast call 0xe9df1e36b7188edaf91b208b9ea6508b2902f517 "totalSupply() returns (uint256)" --rpc-url https://api.harmony.one
```

Response:
```
1000000000000000000000000 [1e24]e
```

### Simple compile script
https://book.getfoundry.sh/forge/deploying

1) Make sure you have the latest version installed
```
foundryup
```

2) Create src/Counter.sol file:
https://docs.openzeppelin.com/cli/2.8/getting-started#your-first-contract

3) Run the deployment script:
```
forge create --gas-limit 5000000 src/Counter.sol:Counter --rpc-url https://api.harmony.one  --private-key <PK> --legacy
```

Full output:
```
[⠊] Compiling...
[⠒] Compiling 1 files with Solc 0.5.17
[⠢] Solc 0.5.17 finished in 77.65ms
Compiler run successful!
Error: 
contract was not deployed
```

NOTE: forge will report "contract was not deployed" error even if the transaction mined

4) Check the explorer
