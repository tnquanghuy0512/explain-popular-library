## 1.1 OZ's Ownable
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol

Summary: An abstract contract that help inheritance contract have a contract owner 

In detail:
    - `Modifier onlyOwner()`: modifier that check if msg.sender is contract's owner or not, if no then it will revert
    - `Function renounceOwnership()`: can only be called by owner, remove ownership of msg.sender, make the contract ownerless
    - `Function transferOwnership(address newOwner)`: can only be called by owner, remove ownership of the caller and set new owner to any address 

How to use:
    - Add modifier onlyOwner for a function that you want to only be called by owner


## 1.2 OZ's Ownable2Step
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable2Step.sol

Summary: Similar to Ownable but when transfering ownership, pending new owner must need an extra step to accept it to become the new owner. This contract existed to prevent transfering ownership to an uncontrolled/wrong address 

In detail:
    - `Modifier onlyOwner()`
    - `Function renounceOwnership()`
    - `Function transferOwnership(address newOwner)`: can only be called by owner, set the pending owner to any address 
    - `Function acceptOwnership()`: can only be called by pending owner, remove current owner, change pending owner (or msg.sender) to become new owner 
How to use:
    - Just like Ownable
    - We need two steps to successfully transfer ownership:
        + Current owner call to transferOwnership()
        + Soon-to-be owner call acceptOwnership()
    <img src="../lib/image/ownable.png">


## 1.3 OZ's AccessControl
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/AccessControl.sol

Summary: When a contract have more than one role,

In detail:
- TODO explain the structure
- TODO explain in hashing

- Exposed function:
    + `modifier onlyRole(bytes32 role)`: modifier that check if msg.sender is contract's role in the input or not, if no then it will revert
    + `function grantRole(bytes32 role, address account)`: can only be called by admin role of the granted role, grant role to input account
    + `function revokeRole(bytes32 role, address account)`: can only be called by admin role of the revoked role, revoke role to input account
    + `function renounceRole(bytes32 role, address callerConfirmation)`: revoke the role of msg.sender



How to use:
- Let say you want to build contract that have 4 role:
    + `DEFAULT_ADMIN_ROLE`: can grant/revoke role for `DEFAULT_ADMIN_ROLE`, `MANAGER`, `3RD_PARTY_ADMIN`
    + `MANAGER`: can grant/revoke role for GUARDIAN
    + `GUARDIAN`:
    + `3RD_PARTY_ADMIN`:
- Here's the diagram of how things should be:
<img src="../lib/image/accessControl.png">
- Here's how we can achieve in code:
```solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.7.0 <0.9.0;

import "@openzeppelin/contracts/access/AccessControl.sol";

contract A is AccessControl {
    bytes32 constant MANAGER = keccak256("MANAGER");
    bytes32 constant GUARDIAN = keccak256("GUARDIAN");
    bytes32 constant THIRD_PARTY_ADMIN = keccak256("THIRD_PARTY_ADMIN");

    constructor() {
        _setRoleAdmin(MANAGER, DEFAULT_ADMIN_ROLE);
        _setRoleAdmin(THIRD_PARTY_ADMIN, DEFAULT_ADMIN_ROLE);
        _setRoleAdmin(GUARDIAN, MANAGER);
    }
}
```
- To build a function that can only be called by a specific role, simply put modifier `onlyRole(bytes32 role)` in the function

## 1.4 OZ's AccessControlEnumerable
https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/extensions/AccessControlEnumerable.sol

Summary: Just like AccessControlEnumerable but we can query all (or with index) user that have a specific role onchain -> TODO

In detail:
- TODO explain different

How to use:
- `function getRoleMember(bytes32 role, uint256 index) public view returns (address)`: return an address with a specific role that in a particular index
- `function getRoleMemberCount(bytes32 role) public view returns (uint256)`: return total number of address that have a specific role
- `function getRoleMembers(bytes32 role) public view returns (address[] memory)`: return all address that have a specific role