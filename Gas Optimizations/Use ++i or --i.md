# Use ++i or --i

`++i` costs less gas than `i++`, especially when it’s used in for-loops (`--i`/`i--` too).

### Example

```solidity
File: smart-contracts/ConvexCurveLPVault.sol

106:      for (uint256 i = 0; i < extraRewardsLength; i++) {...}
```

### Recommendation

```solidity
File: smart-contracts/ConvexCurveLPVault.sol

106:      for (uint256 i = 0; i < extraRewardsLength; ++i) {...}
```
