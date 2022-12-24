# make-your-frist-DApp-using-solidity-programming-language-


pragma solidity ^0.7.0;

// This contract represents a simple token
// that can be transferred between accounts
contract SimpleToken {
    // The total supply of the token
    uint public totalSupply;

    // The balance of each account
    mapping(address => uint) public balanceOf;

    // The name of the token
    string public name;

    // The symbol of the token
    string public symbol;

    // The number of decimals of the token
    uint public decimals;

    // The constructor function is called when
    // the contract is deployed
    constructor(
        uint initialSupply,
        string memory tokenName,
        string memory tokenSymbol,
        uint tokenDecimals
    ) public {
        totalSupply = initialSupply;
        balanceOf[msg.sender] = totalSupply;
        name = tokenName;
        symbol = tokenSymbol;
        decimals = tokenDecimals;
    }

    // This function allows a user to transfer
    // tokens to another account
    function transfer(
        address to,
        uint value
    ) public {
        // Make sure the sender has enough tokens
        require(balanceOf[msg.sender] >= value, "Insufficient balance");

        // Make sure the recipient is not the contract itself
        require(to != address(0), "Invalid recipient");

        // Transfer the tokens
        balanceOf[msg.sender] -= value;
        balanceOf[to] += value;
    }
}
