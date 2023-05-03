## Ali_Khatami_Solidity_08
### Interfaces and Price Feeds

given a code

```
//SPDX-License-Identifier:MIT

pragma solidity ^0.8.8;

contract akrkFundMe  {

    uint256 public minimumUSD=50;

// we have use payable keyword with the function below to make it payable with any native blockchain currency
    function fund() public payable {

        require(msg.value >= minimumUSD , "Not send enough");// to get accees to the 'value' at deploy at run transaction tab
        //1e18 is 1 ether, here the value must be greater than 1 ether
        //require is a checker it checks whether the value is greater than 1 ether
        // if not it is going to revert with an error messsage shown above

    }// To send money. We made it public so that anybody can call it



    

}
```

In the code above if ```msg.value``` is actually greater than minimum USD we have to convert that msg.value from it's layer one slash ethereum to USD equivalent.<br>

for that first we need to get the price of ethereum or whatever layer one blockchain we are working with<br>




