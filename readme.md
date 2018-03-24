# README #



### What is this repository for? 

* L-Pesa ICO contract
* ver 1.0
* for crowdfunding during the pre and ICO phases


### How do I get set up?  

* There is main crowdfunding contracts responsible for this ICO presale and public sale.
**Crowdsale.sol**

* Use truffle, Ethereum Wallet or Remix to deploy contract on Ethereum network.
* Deploy **Crwodsale** contract and obtain its address. 
* Deploy **Token** contract and use address from previous step and use it as its inputs. Obtain address of the token contract.  
* Call function **setTokenAddress()** of **Crowdsale**  contract and provide address from Token contract as its input.


### How do I run

* owner can start the contract by calling **start()** function. Argument provided to the **start()** function is number of blocks. Average block time on main net is around 14 seconds as of this writing.  

* contributions are accepted by sending ether to contract address and tokens are instantly sent back to contributors. 

* when the campaign is over, admin can run **finilize()** function to end the campaign. 

* in case of emergency function **emergencyStop()** can be called to stop contribution and function **release()** to start campaign again.  


* option to withdraw contributions is provided in case ICO was not successful. Minimum cap hasn't been reached.
 contributors can call function **refund()** to return the tokens and receive back their contribution. 

* in order for contributors to be able to get refunds, following conditions have to be met.  

    1. Current block number has to be higher then endBlock. 
    2. Campaign did't reach minCap.
    3. Flag **isRefunding** needs to be set to true using **prepareRefund()** function.  Function will expect exact amount of money which the sale has collected.

* During ICO tokens are in the locked stage. In order to be able to transfer tokens, admin has to call function **unlock()** of token contract. 
