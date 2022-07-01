# Declare Public Functions Not Used By Contract As External

`public` functions not called by the contract should be declared `external` instead.

Contracts are allowed to override their parents’ functions and change the visibility from `external` to `public` and can save gas by doing so.

### Example

```solidity
File: smart-contracts/CollateralAdapter.sol   #1

35:     function initialize(ILendingPoolAddressesProvider _provider) public initializer {...}
```
