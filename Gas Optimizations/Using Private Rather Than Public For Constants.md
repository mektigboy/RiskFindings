# Using Private Rather Than Public For Constants

Using `private` rather than `public` for constants, saves gas.

If needed, the value can be read from the verified contract source code. Savings are due to the compiler not having to create non-payable getter functions for deployment calldata, and not adding another entry to the method ID table.

### Example

```solidity
File: smart-contracts/CollateralAdapter.sol

22:     uint256 public constant VAULT_REVISION = 0x1;
```

### Recommendation

```solidity
File: smart-contracts/CollateralAdapter.sol

22:     uint256 private constant VAULT_REVISION = 0x1;
```
