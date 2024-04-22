## 4.2 Math
## 4.2.1 OZ's SafeCast
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SafeCast.sol
Summary: A library that support downcasting uint256/int256 that can reverted 

In detail:

- `uint256 a = type(uint32).max + 5 = 4294967300`
- `uint32(a)` returning `4` 
- `SafeCast.toUint32(a)` got reverted

Exposed function:
- TODO

How to use:
## 4.2.2 OZ's Math
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/Math.sol

Summary: A helper library that help on calculating and stuffs

In detail:

Exposed function:
- TODO



How to use:
## 4.2.3 OZ's SignedMath
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/math/SignedMath.sol

Summary:

In detail:

How to use:
## 4.2.4 PaulRBerg's Math
https://github.com/PaulRBerg/prb-math
Summary:

In detail:

How to use: