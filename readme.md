# README #



### What is this repository for? 

* L-Pesa ICO contract
* ver 1.0
* for crowdfunding during the pre and ICO phases


### How do I get set up?  

* Use truffle, Ethereum Wallet or Remix to deploy contract on Ethereum network.
* First deploy **Crwodsale** contract and obtain its address.  
* Secondly deploy **Token** contract and use address from previous step as its input. Obtain address of the token contract.  
* Thirdly call function **updateTokenAddress()** of **Crowdsale** contract and provide address from Token contract as its input.


### How do I run

* owner can start the contract by calling **start()** function. Argument provided to the **start()** function is number of blocks. Average block time on main net is around 14 seconds as of this writing.  

* contributions are accepted by sending ether to contract address 

* when contract is deployed first, it is configured to act as a presale contract.  

* to switch contract to public ICO mode call **advanceStep()** function to set public ICO mode.  
*Be careful as there is no way to switch back to presale.*

* to decrease bonus call function **decreaseBonus()**. This function will lower the bonus. This is only one way function and once bonus is decreased it can't 
be switched back. 

* when the campaign is over, admin can run **finilize()** function to end the campaign and transfer unsold and dev tokens to individual wallet.  
During finalize, token contract is unlocked and contributors can start trading tokens. 

* in case of emergency function **emergencyStop()** can be called to stop contribution and function **release()** to start campaign again.  

* option to withdraw contributions is provided in case ICO was not successful. Minimum cap hasn't been reached.
 contributors can call function **refund()** to burn the tokens and receive back their contribution. 

* in order for contributors to be able to get refunds, following conditions have to be met.  

    1. Current block number has to be higher then endBlock. 
    2. Campaign did't reach minCap.
    3. Step has to be set to **Step.Refunding** using **prepareRefund()** function.  Function will expect exact amount of money which both presael and public ICO received during the campaign. 

* During ICO tokens are in the locked stage. In order to be able to transfer tokens, admin has to call function **unlock()** of token contract. 
