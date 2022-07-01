# No Empty Blocks

Empty blocks should be removed or emit something.

The code should be refactored such that they no longer exist, or the block should do something useful, such as emitting an event or reverting. If the contract is meant to be extended, the contract should be `abstract` and the function signatures be added without any default implementation. If the block is an empty if-statement block to avoid doing subsequent checks in the else-if/else conditions, the else-if/else conditions should be nested under the negation of the if-statement, because they involve different classes of checks, which may lead to the introduction of errors when the code is later modified (`if(x){}else if(y){...}else{...}` => `if(!x){if(y){...}else{...}}`).

```solidity
File: smart-contracts/GeneralVault.sol

153:    function processYield() external virtual {}

158:    function pricePerShare() external view virtual returns (uint256) {}

246:    {}

255:    ) internal virtual returns (uint256) {}

265:    {}
```
