// SPDX-License-Identifier: MIT
import "./Repeat.sol";
import "./Destruction.sol";
pragma solidity ^0.8.15;
contract Hype  {
    School [] public Detail;
    struct School {
        string name;
        string caste;
        uint age;
        uint percentage;
    }
    function detail (string memory name,string memory caste,uint age,uint percentage) public {
        Detail.push(School(name,caste,age,percentage));
    }
    function Size() public view returns(uint) {
        return Detail.length;
    }
    function Remove(uint Erase) public {
        delete Detail[Erase];
    }
}
    contract Mapping is Hype,Check,Destruction {
    mapping(address => uint) Getting;

    event Trading (address From,address To,uint Amount);
    function AddBalance() payable public returns(uint) {
        emit Trading (msg.sender,msg.sender,msg.value);
        Getting[msg.sender] = msg.value;
        return Getting[msg.sender];
    }
    function withdrawal (uint amount) public returns (uint) {
        require (Getting[msg.sender] >= amount,"Insufficient Balance");
        payable(msg.sender).transfer (amount);
        Getting[msg.sender] -= amount;
        return Getting[msg.sender];
    }
    function GetBalance() public view returns(uint) {
        return Getting[msg.sender];
    }
    function GetTotalBalance () public view returns (uint) {
        return address(this).balance;
    }
    function Transfer (address Received, uint Amount) public onlyowner {
        require (Getting[msg.sender] >= Amount,"You Dont Have Balance To Send");
        require (msg.sender != Received,"Cant Possible");
        uint previousbalance = Getting[msg.sender];
        Getting[msg.sender] -= Amount;
        Getting[Received] += Amount; 
        assert (Getting[msg.sender] == previousbalance - Amount);
    }
}
