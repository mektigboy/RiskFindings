# Use More Recent Solidity Version

Use a more recent version of solidity.

- Use a Solidity version of at least 0.8.0 to get overflow protection without `SafeMath`.
- Use a Solidity version of at least 0.8.2 to get compiler automatic inlining.
- Use a Solidity version of at least 0.8.3 to get better `struct` packing and cheaper multiple storage reads.
- Use a Solidity version of at least 0.8.4 to get custom errors, which are cheaper at deployment than `revert()`/`require()` strings.
- Use a Solidity version of at least 0.8.10 to have external calls skip contract existence checks if the external call has a return value.
