[#2025-03-20 Thu: Total Strategy Yield Recalculation](#2025-03-20):
#### Total Strategy Yield Recalculation
<img width="554" alt="image" src="https://github.com/user-attachments/assets/3ebc4bb5-0919-4633-a194-703878e2a7b1" />

[#2025-03-11 Tue: Sonic-yield-calculator + 1Bot models](#2025-03-11)
<img width="1366" alt="image" src="https://github.com/user-attachments/assets/4d413f47-be33-40fa-a007-4381888804c1" />

[# 2025-03-010 Mon: Sonic-yield-calculator + 1Bot models](#2025-03-10)
### Sonic Yield Calculator
<img width="1071" alt="image" src="https://github.com/user-attachments/assets/1c381efa-f2b6-4f69-be64-eac3926771e9" />

### 1Bot models
![image](https://github.com/user-attachments/assets/023a4cb7-8ad8-4fcc-9a2e-f83a1317e9d5)


[# 2025-03-07 Fri: FarmStrategy.sol contract](#2025-03-07)

##  FarmStrategy.sol Contract Summary

### Core Purpose
A strategy module in the Sickle system that manages farming operations across DeFi protocols.

### Key Functions
- **Deposit/Increase**: Adds tokens to farming positions
- **Compound**: Claims rewards and reinvests them
- **Harvest**: Claims rewards without reinvesting
- **Withdraw**: Removes tokens from farming positions
- **Exit**: Combines harvest and withdraw operations

### Automation Capabilities
- **harvestFor**: Claims rewards for a user automatically
- **compoundFor**: Compounds positions automatically
- **exitFor**: Performs exit operations automatically

### Architecture
- Inherits from StrategyModule
- Implements IAutomation and FarmStrategyEvents interfaces
- Uses specialized libraries for token transfers, swaps, fees, liquidity operations, and position settings

### Key Components
- **Position Settings Registry**: Tracks and validates configuration for different farms
- **Multicall Pattern**: Batches multiple operations into a single transaction
- **Modular Design**: Uses specialized libraries for different functions

### Rebalancing Mechanism
- Implemented primarily through the _compound function
- Claims rewards from one position
- Reinvests into same or different position
- Uses zapping to optimize token swaps and liquidity provision

This contract essentially acts as the operational center for automated farming strategies, allowing users to optimize their yield farming through automated compounding, harvesting, and position management.

---
# 2025-03-06 Thu: Token icon is not shown. 
<img width="1432" alt="image" src="https://github.com/user-attachments/assets/bd62e580-b329-4cfb-9bb6-74b03ab72b81" />

---
# 2025-03-05 Wed: Current UI implementation as of March 5th. Sheet cell interaction functionality planned for next iteration.

<img width="1253" alt="image" src="https://github.com/user-attachments/assets/f6dfb61a-02c0-4de1-b1e8-07ef2eab8883" />

