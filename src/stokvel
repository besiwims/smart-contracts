
// SPDX-License-Identifier: MIT

pragma solidity 0.6.8;


interface IStokvel {
    function showStockvelName() external view returns (string memory);
}

contract Stokvel is IStokvel {
    
    struct Account {
        uint32 id;
        address member;
        bytes32 memberSecretString;
        uint32 amount;
     }
      
    mapping(address => Account) private members;
    
    string  groupName;
    
    mapping(uint32 => address) private memberIDs;
    
    uint32 private stockvelTotalAmount = 0;

    uint32 private lastId;
    
    address internal owner;
    
    function register(address   _addr, string calldata _memberSecretString, uint32   _amount)   external returns (bool)  {
        
        //require(!members[_addr].exists, "Already a member!");
        
        bool result = false;

        lastId++;
        
        stockvelTotalAmount += _amount;
    
        members[_addr] = Account({
    								id: lastId, 
    								member: _addr, 
    								memberSecretString :  keccak256(abi.encodePacked(_memberSecretString)),
    								amount : _amount
    							});
    		
        memberIDs[lastId] = _addr;
        
        //emit Registration(_addr, lastId, _sponsor);
        
        
        return result;
  }
  
    function showAccountDetails(address _addr) external view returns(uint32, address , uint32 ){
        return (members[_addr].id , members[_addr].member , members[_addr].amount);
        
    }
    
    function showAccountAddress(uint32 _id) external view returns(address){
        return (memberIDs[_id]);
        
    }
    
    function showAccountDetailsFromId(uint32 _id) external view returns(uint32, address , uint32 ){
        return (members[memberIDs[_id]].id , members[memberIDs[_id]].member , members[memberIDs[_id]].amount);
        
    }
   
    function showStokvelTotalAmount() external view returns(uint32 ){
        return stockvelTotalAmount;
        
    }
    
    function showTotalMembers() external view returns(uint32 ){
        return lastId;
        
    }
    
    constructor(string memory _name) public {
         owner = msg.sender;
         groupName = _name;
    }
  
  function  showStockvelName()  public view override returns (string memory){
      return groupName;
  }
  
  
}
