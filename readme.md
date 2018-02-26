# README #



### What is this repository for? 

* L-Pesa ICO contract
* ver 1.0
* for crowdfunding during the pre and ICO phases


### How do I get set up?  

* There are two main crowdfunding contracts responsible for this ICO.
* **Presale.sol** and **Crwodsale.sol**
* Both contracts are similar in their logic, with the difference that they have different dates of releasing tokens.
The reqirement to offer vesting options has been requested when contract was developed and to offer this option without redesigning
the entire contract, one contract has been duplicated and modified accordingly. 
Now each of thme has optoin to release their tokens at differnt dates. 

* Use truffle, Ethereum Wallet or Remix to deploy contract on Ethereum network.
* First deploy **Presale** contract and obtain its address. 
* Conduct contribution to above contract.  
* Then deploy **Crwodsale** contracct and obtain its address. 
* Conduct contributions to above contract. 
* Thirdly deploy **Token** contract and use address from previous two step and use them as its inputs. Obtain address of the token contract.  
* Thirdly call function **updateTokenAddress()** of **Crowdsale** and **Presale** contract and provide address from Token contract as its input.


### How do I run

* owner can start the contract by calling **start()** function. Argument provided to the **start()** function is number of blocks. Average block time on main net is around 14 seconds as of this writing.  

* contributions are accepted by sending ether to contract address 

* when the campaign is over, admin can run **finilize()** function to end the campaign. 

* in case of emergency function **emergencyStop()** can be called to stop contribution and function **release()** to start campaign again.  

* option to claim tokens by contributors is provided to claim their tokens after vesting period.
 Usres need to call function **claimTokens()** from the address from which they have made contributions. 

* option to withdraw contributions is provided in case ICO was not successful. Minimum cap hasn't been reached.
 contributors can call function **refund()** to return the tokens and receive back their contribution. 

* in order for contributors to be able to get refunds, following conditions have to be met.  

    1. Current block number has to be higher then endBlock. 
    2. Campaign did't reach minCap.
    3. Flag **isRefunding** needs to be set to true using **prepareRefund()** function.  Function will expect exact amount of money which the sale has collected.

* During ICO tokens are in the locked stage. In order to be able to transfer tokens, admin has to call function **unlock()** of token contract. 
