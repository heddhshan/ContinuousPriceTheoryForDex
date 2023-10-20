# ContinuousPriceTheoryForDex
Comparing Uniswap, a new liquidity algorithm for decentralized exchanges


1，Uniswap’s algorithm

Here is a brief review of Uniswap’s liquidity identity algorithm. For simplicity, UniswapV1V2 will be used for illustration.
For the trading pair TokenA=>TokenB, the corresponding liquidity is X and Y, then X*Y=K. When trading, X or Y will change, but the K value remains unchanged.
Assuming that the original liquidity is X0 and Y0, and the user pays dY amount of TokenB to purchase x amount of TokenA, the liquidity formula needs to be satisfied: X0 * Y0 = (X0 - x) * (Y0 + dY), which can be derived
x =Ｘ0 -(︸0 * Y0 )/ (Y0 + dY)- X0=(X0* dY)/ (Y0 + dY)

That is (Formula 1) 	x =(X0* dY)/ (Y0 + dY)


2，He's new algorithm (continuous price theory)

The core logic is: do not use x*y=k to deduce the transaction quantity, but use the price to deduce it.
After the purchase, the price has two forms of expression. The purchase price is: bPrice = x / dY; and the price of the remaining liquidity is: lPrice = (X0-x) / (Y0+dy). Of course, the two prices are the same (this is the core point), then x / dY = (X0-x) / (Y0+dy), which can be derived
x * (Y0+dy) = (X0-x) * dY
x * (Y0+2 * dy) = X0 * dY

That is (Formula 2) 	x =(X0* dY)/ (Y0 + 2 * dY)

Has anyone considered this algorithm? I haven't seen anyone propose this algorithm in the Chinese community. Other famous DEXs do not use this algorithm, such as PancakeSwap, dXdY, etc.



3，Expand He's algorithm (continuous price theory)
If there is a trading pool containing TokenA, TokenB, and TokenC, it is possible to trade any trading pair among these three Tokens.
There is a problem in this situation. When trading TokenA and TokenB, the other two trading pairs TokenA=>TokenC and TokenB=>TokenC do not trade at all, but the prices change (one goes up and the other goes down). Because TokenA and TokenB in the corresponding pool have changed. 
This approach avoids arbitrage and MEV.



可以参看中文文档：
https://learnblockchain.cn/article/6709
