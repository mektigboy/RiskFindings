# Mark Functions Guaranteed To Revert As Payable

Functions guaranteed to revert when called by normal users can be marked `payable`.

If a function modifier such as `onlyOwner` is used, the function will revert if a normal user tries to pay the function. Marking the function as `payable` will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. The extra opcodes avoided are
`CALLVALUE`(2),`DUP1`(3),`ISZERO`(3),`PUSH2`(3),`JUMPI`(10),`PUSH1`(3),`DUP1`(3),`REVERT`(0),`JUMPDEST`(1),`POP`(2), which costs an average of about 21 gas per call to the function, in addition to the extra deployment cost.

### Example

```solidity
File: smart-contracts/CollateralAdapter.sol

43      function addCollateralAsset(
44        address _externalAsset,
45        address _internalAsset,
46        address _acceptVault
47:     ) external onlyAdmin {
```
