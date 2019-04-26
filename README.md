# bondedstake

## Context

The Livepeer Token (LPT) is an ERC-20 Token on Ethereum, used to secure the Livepeer Protocol.

Livepeer's Protocol provides incentives to LPT holders to bond these tokens to a node in Livepeer's network.

When a holder unbonds LPT from the node, they must wait for an _unbonding period_ before they can withdraw the LPT.

During this _unbonding period_, the holder does not receive any rewards.

## Starting Situation

Alice has TokenA.

Bob has LPT, bonded to a node in Livepeer's network. Bob also has TokenB.

TokenA can be Ether or an ERC-20 Token.

TokenB can be Ether or an ERC-20 Token.

## Objective

Alice would like to exchange `x` TokenA for `y` LPT.

## Use Cases

These scenarios describe the _only_ scenarios which should be possible using this system.

### Scenario 1

1. Alice deposits `x` TokenA into the contract, specifying

* `y` = the amount of LPT to be received in exchange for `x` TokenA
* `z` = the amount of TokenB to be provided as security, and
* `t` = the block number by which Alice wants to receive the LPT

2. Alice withdraws `x` TokenA.

### Scenario 2

1. Alice deposits `x` TokenA into the contract, specifying

* `y` = the amount of LPT to be received in exchange for `x` TokenA
* `z` = the amount of TokenB to be provided as security, and
* `t` = the block number by which Alice wants to receive the LPT

2. Bob deposits `z` TokenB.
_Note: after this step, Alice cannot withdraw TokenA until time `t` has passed_

3. Block `t` is mined.

4. Alice withdraws `x` TokenA, and receives `z` TokenB

### Scenario 3 - Main Success Scenario

1. Alice deposits `x` TokenA into the contract, specifying

* `y` = the amount of LPT to be received in exchange for `x` TokenA
* `z` = the amount of TokenB to be provided as security, and
* `t` = the block number by which Alice wants to receive the LPT

2. Bob deposits `z` TokenB.
_Note: after this step, Alice cannot withdraw TokenA until time `t` has passed_

3. Bob deposits `y` LPT _before_ block `t`, and receives `x` TokenA and `z` TokenB.

4. Alice withdraws `y` LPT.
