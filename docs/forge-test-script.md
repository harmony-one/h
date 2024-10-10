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
