﻿# Vesting Schedule Implementation (VestingSchedule.sol)

**contract VestingSchedule is [VestingScheduleBase](VestingScheduleBase.md), [FrequencyHelper](FrequencyHelper.md)**

**VestingSchedule**

Vesting Schedule indicates when, how much, and how frequently
founders, employees, and advisors can exercise their token allocations.
Vesting is determined for each individual.

## Constructor

Constructs this contract

```js
constructor(uint256 _minPeriod, uint256 _withdrawalCap, ERC20 _vestingCoin) public
```

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _minPeriod | uint256 | The minimum vesting period. | 
| _withdrawalCap | uint256 | Maximum amount of tokens that can be withdrawn for the specified frequency. | 
| _vestingCoin | ERC20 | The ERC20 contract of the coin being vested. | 

## Modifiers

- [canWithdraw](#canwithdraw)

### canWithdraw

Signifies if the sender has enough balances to withdraw the desired amount of the vesting coin.

```js
modifier canWithdraw(uint256 _amount) internal
```

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _amount | uint256 | The amount desired to be withdrawn. | 

## Functions

- [fund](#fund)
- [removeFunds](#removefunds)
- [createAllocation](#createallocation)
- [deleteAllocation](#deleteallocation)
- [increaseAllocation](#increaseallocation)
- [decreaseAllocation](#decreaseallocation)
- [extendAllocation](#extendallocation)
- [getDrawingPower](#getdrawingpower)
- [withdraw](#withdraw)

### fund

Enables this vesting schedule contract to receive the ERC20 (vesting coin).
Before calling this function please approve your desired amount of the coin
for this smart contract address.
Please note that this action is restricted to administrators only.

```js
function fund() external
returns(bool)
```

**Returns**

Returns true if the funding was successful.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|

### removeFunds

Allows you to withdraw the surplus balance of the vesting coin from this contract.
Please note that this action is restricted to administrators only
and you may only withdraw amounts above the sum total allocation balances.

```js
function removeFunds(uint256 _amount) external
returns(bool)
```

**Returns**

Returns true if the withdrawal was successful.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _amount | uint256 | The amount desired to withdraw. | 

### createAllocation

Creates a vesting schedule allocation for a new beneficiary.
A beneficiary could mean founders, employees, or advisors.
Please note that this action can only be performed by an administrator.

```js
function createAllocation(address _address, string _memberName, uint256 _amount, uint256 _releaseOn) external
returns(bool)
```

**Returns**

Returns true if the vesting schedule allocation was successfully created.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _address | address | The address which will receive the tokens in the future date. | 
| _memberName | string | The name of the candidate for which this vesting schedule allocation is being created for. | 
| _amount | uint256 | The total amount of tokens being vested over the period of vesting duration. | 
| _releaseOn | uint256 | The date on which the first vesting schedule becomes available for withdrawal. | 

### deleteAllocation

Deletes the specified vesting schedule allocation.
Please note that this action can only be performed by an administrator.

```js
function deleteAllocation(address _address) external
returns(bool)
```

**Returns**

Returns true if the vesting schedule allocation was successfully deleted.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _address | address | The address of the beneficiary whose allocation is being requested to be deleted. | 

### increaseAllocation

Increases the total allocation of the specified vesting schedule.
Please note that this action can only be performed by an administrator.

```js
function increaseAllocation(address _address, uint256 _additionalAmount) external
returns(bool)
```

**Returns**

Returns true if the vesting schedule allocation was successfully increased.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _address | address | The address of the beneficiary whose allocation is being requested to be increased. | 
| _additionalAmount | uint256 | The additional amount in vesting coin to be addeded to the existing allocation. | 

### decreaseAllocation

Decreases the total allocation of the specified vesting schedule.
Please note that this action can only be performed by an administrator.

```js
function decreaseAllocation(address _address, uint256 _lessAmount) external
returns(bool)
```

**Returns**

Returns true if the vesting schedule allocation was successfully decreased.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _address | address | The address of the beneficiary whose allocation is being requested to be decreased. | 
| _lessAmount | uint256 | The amount in vesting coin to be decreased from the existing allocation. | 

### extendAllocation

Extends the release date of the specified vesting schedule allocation.
Please note that this action can only be performed by an administrator.

```js
function extendAllocation(address _address, uint256 _newReleaseDate) external
returns(bool)
```

**Returns**

Returns true if the vesting schedule allocation was successfully extended.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _address | address | The address of the beneficiary who allocation is being requested to be extended. | 
| _newReleaseDate | uint256 | A new release date to extend the allocation to. | 

### getDrawingPower

Gets the drawing power of the beneficiary.

```js
function getDrawingPower(address _address) public
returns(uint256)
```

**Returns**

Returns the amount in vesting coin that can be withdrawn.

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _address | address | The address to check the drawing power of. | 

### withdraw

This action enables the beneficiaries to withdraw a desired amount from this contract.

```js
function withdraw(uint256 _amount) external
returns(bool)
```

**Arguments**

| Name        | Type           | Description  |
| ------------- |------------- | -----|
| _amount | uint256 | The amount in vesting coin desired to withdraw. | 

## Contracts

- [ERC20Basic](ERC20Basic.md)
- [VestingSchedule](VestingSchedule.md)
- [SafeMath](SafeMath.md)
- [BasicToken](BasicToken.md)
- [StandardToken](StandardToken.md)
- [CustomPausable](CustomPausable.md)
- [VestingScheduleBase](VestingScheduleBase.md)
- [CustomAdmin](CustomAdmin.md)
- [Migrations](Migrations.md)
- [StandardTokenMock](StandardTokenMock.md)
- [FrequencyHelper](FrequencyHelper.md)
- [Ownable](Ownable.md)
- [ERC20](ERC20.md)
