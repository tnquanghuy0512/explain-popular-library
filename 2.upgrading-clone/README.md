# 2. Upgrading/Clone/Deploying

First of all, if you don't understand those following term, please go to this page for more (detail)[TERM_EXPLAIN]:
- Transparent
- UUPS
- BeaconProxy wtf
- Diamond

- Normal CREATE
- CREATE2
- CREATE3

- Cloning

## 2.1 OZ's ERC1967Proxy
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/ERC1967/ERC1967Proxy.sol

Summary:

In detail:

How to use:
## 2.2 OZ's BeaconProxy
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/beacon/BeaconProxy.sol


Summary:

In detail:

How to use:
## 2.3 OZ's TransparentProxy
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/transparent/TransparentUpgradeableProxy.sol


Summary:

In detail:

How to use:
## 2.4 OZ's UUPSProxy
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/utils/UUPSUpgradeable.sol


Summary:

In detail:

How to use:


## 2.5 OZ's Upgradable contract version
https://github.com/OpenZeppelin/openzeppelin-upgrades

## 2.5 OZ's CREATE2
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/Create2.sol

Summary: A helper library that helps deploying new contracts with salt and calculate soon-to-be-deployed contract address with salt 


In detail:
- TODO what's create2
- CREATE

- Exposed function:
    + `function deploy(uint256 amount, bytes32 salt, bytes memory bytecode) internal returns (address addr)`
    + `function computeAddress(bytes32 salt, bytes32 bytecodeHash) internal view returns (address)`
    + `function computeAddress(bytes32 salt, bytes32 bytecodeHash, address deployer) internal pure returns (address addr)`


How to use:
- Note: In solidiy version 0.6.2, create2 can now easy to achieve in high level with this syntax: `new Contract{salt: 0x1234}(arg1, arg2)`



## 2.6 Solady's CREATE3
https://github.com/Vectorized/solady/blob/main/src/utils/CREATE3.sol

Summary:

In detail:

How to use:

## 2.7 OZ's Clones
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/proxy/Clones.sol

Summary:

In detail:

How to use:

## 2.8 Wighawag's Clones with immutable args
https://github.com/wighawag/clones-with-immutable-args?tab=readme-ov-file

Summary:

In detail:

How to use: