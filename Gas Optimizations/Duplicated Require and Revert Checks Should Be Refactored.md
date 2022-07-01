# Duplicated Require and Revert Checks Should Be Refactored

Duplicated `require()`/`revert()` checks should be refactored to a modifier or function.

### Example

```
File: smart-contracts/ConvexCurveLPVault.sol   #1

101:      require(_token == _tokenFromConvex, Errors.VT_INVALID_CONFIGURATION);
```

# Duplicated Require and Revert Checks Should Be Refactored

Duplicated `require()`/`revert()` checks should be refactored to a modifier or function.

### Example

```
File: smart-contracts/ConvexCurveLPVault.sol   #1

101:      require(_token == _tokenFromConvex, Errors.VT_INVALID_CONFIGURATION);
```
