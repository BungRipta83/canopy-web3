// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract CanopyStaking {
    mapping(address => uint256) public stakes;

    event Staked(address indexed user, uint256 amount);
    event Withdrawn(address indexed user, uint256 amount);

    function stake() public payable {
        require(msg.value > 0, "Must send ETH");
        stakes[msg.sender] += msg.value;
        emit Staked(msg.sender, msg.value);
    }

    function withdraw(uint256 amount) public {
        require(stakes[msg.sender] >= amount, "Not enough balance");

        stakes[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);

        emit Withdrawn(msg.sender, amount);
    }
}
