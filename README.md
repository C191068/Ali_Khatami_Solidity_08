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

If we want to interact any contract which is outside of our contract we need two things<br> 
1.ABI<br>
2.Address of our contract<br>

![f43](https://user-images.githubusercontent.com/89090776/235877819-4ef2e9a4-b321-4522-85a1-d900ada04c1e.jpg)
Figure1: we can find the addresses of the contract by going to this site https://docs.chain.link/ at this section<br>

We can find the ABI if we find an example of interface in the following way:

![f44](https://user-images.githubusercontent.com/89090776/235881026-4220e5d6-8079-452a-ad63-7996fef9cd16.jpg)
Figure2: at first we will go to this link https://github.com/smartcontractkit/chainlink and click the contracts folder<br>

![f45](https://user-images.githubusercontent.com/89090776/235881736-613223cb-21f9-49d8-a16f-e4f8bd7f65f4.jpg)
Figure3: then we will click the src folder<br>

![f46](https://user-images.githubusercontent.com/89090776/235882103-fdfc20bf-844d-41de-b792-13f94a82865d.jpg)
Figure4: Then we click the v0.8 folder <br>

![f47](https://user-images.githubusercontent.com/89090776/235882757-2ea4ebff-c142-4b51-bdb5-97171d90c46d.jpg)
Figure5: then we will click on ```AggregatorV3Interface.sol``` folder <br>



![f48](https://user-images.githubusercontent.com/89090776/235884759-cc1ff218-0fe8-4532-9e9d-665ef19d4f6f.jpg)
Figure6:here we can see a whole bunch of function declraration but no logic is implemented in these functions<br>
this is what known as interface,if we compile these we will get the ABI of a contract as it defines all the different<br>
ways we can interact with the contract<br>


![f49](https://user-images.githubusercontent.com/89090776/235886375-d60dd0c2-543a-4438-9183-6ea338fa1fa8.jpg)
Figure7: We will copy the code from below ```pragma solidity ^0.8.0``` upto the bottom<br>


![f51](https://user-images.githubusercontent.com/89090776/235888496-d3317c68-b51b-41bc-97a7-4c4f89f582d4.jpg)\
Figure8: Then we wil paste it at our solidity file ```FundMe.sol``` below ```pragma solidity ^0.8.8```<br>




```
//SPDX-License-Identifier:MIT

pragma solidity ^0.8.8;

interface AggregatorV3Interface {
  function decimals() external view returns (uint8);

  function description() external view returns (string memory);

  function version() external view returns (uint256);

  function getRoundData(uint80 _roundId)
    external
    view
    returns (
      uint80 roundId,
      int256 answer,
      uint256 startedAt,
      uint256 updatedAt,
      uint80 answeredInRound
    );

  function latestRoundData()
    external
    view
    returns (
      uint80 roundId,
      int256 answer,
      uint256 startedAt,
      uint256 updatedAt,
      uint80 answeredInRound
    );
}

contract akrkFundMe  {

    uint256 public minimumUSD=50;

// we have use payable keyword with the function below to make it payable with any native blockchain currency
    function fund() public payable {

        require(msg.value >= minimumUSD , "Not send enough");// to get accees to the 'value' at deploy at run transaction tab
        //1e18 is 1 ether, here the value must be greater than 1 ether
        //require is a checker it checks whether the value is greater than 1 ether
        // if not it is going to revert with an error messsage shown above

    }// To send money. We made it public so that anybody can call it

  //The function below is created so that we can get price of ethereum in terms of USD , so that we can convert msg.value to USD
//Both functions are public because we can do whatever we want with them
//By using the getPrice() function below we are going to interact with contract outside of our project

    function getPrice() public {

        //ABI
        //Address 0x694AA1769357215DE4FAC081bf1f309aDC325306
    }

    function getConversionRate()  public {}
    

}
```

we can use ```interface AggregatorV3Interface``` to make API calls




