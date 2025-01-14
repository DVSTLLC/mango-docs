# 💀 Liquidations

* Liquidations occur when account Maintenance Health is below 0
* Partial Liquidations are possible&#x20;
* Liquidations are permissionless and open to anyone for a liquidation fee reward

## Liquidations

Every `MangoAccount` must have a `maint_health` above zero. If it slips below zero, liquidators can start liquidating the account until the `init_health` is above zero. The liquidator may forcibly cancel all open orders and start paying off liabilities in the account and withdrawing the assets (defined as positive perp balances or token deposits) in the account. The liquidator earns the `liquidation_fee` which&#x20;

If, at the end of a Liquidate instruction the account has no more assets , but still has liabilities, then the account is placed under bankruptcy. During bankruptcy, the liquidator continues offsetting liabilities, but receives USDC from the insurance fund. Finally, if there is no more USDC in the insurance fund, there will be a socialize loss event (described below). There are seven liquidation related instructions that can be called on Mango V3:

* ForceCancelSpotOrders
* ForceCancelPerpOrders
* LiquidateTokenAndToken
* LiquidateTokenAndPerp
* LiquidatePerpMarket
* ResolveTokenBankruptcy
* ResolvePerpBankruptcy
