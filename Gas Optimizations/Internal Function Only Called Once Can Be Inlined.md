# Internal Functions Only Called Once Can Be Inlined

Not inlining costs 20 to 40 gas because of two extra JUMP instructions and additional stack operations needed for function calls.

### Example

```solidity
function _sharesToTokens(uint256 _sharesAmount) internal view returns (uint256) {
    return _sharesAmount.mul(vault.getPricePerFullShare()).div(1e18);
}
```

```solidity
function _tokensToShares(uint256 _tokensAmount) internal view returns (uint256) {
    return _tokensAmount.mul(1e18).div(vault.getPricePerFullShare());
}
```

The internal functions \_sharesToTokens and \_tokensToShares are both being used only once. Inline them can reduce code size and save gas.

**Recommendation**

Remove `_sharesToTokens()` and `_tokensToShares()` and change `totalValue()` and `withdraw()` to:

```solidity
function totalValue() external view override returns (uint256) {
    return IDetailedERC20(vault.getLPToken()).balanceOf(address(this))
        .mul(vault.getPricePerFullShare()).div(1e18);
}
```

```solidity
function withdraw(address _recipient, uint256 _amount) external override onlyAdmin {
    vault.withdraw(
        _amount.mul(1e18).div(vault.getPricePerFullShare())
    );
    address _token = vault.getToken();
    IDetailedERC20(_token).safeTransfer(_recipient, _amount);
}
```
