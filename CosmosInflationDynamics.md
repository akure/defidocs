
# Cosmos Inflation Dynamics

## What is Inflation?

- To understand the inflation dynamic in the cosmos-hub-chain; it is important to first understand the inflation in the blockchain space.
Inflation and Inflation rate are interchangeable words in this space. Inflation means to inflat; means to grow to make something larger.

- In any application specific blockchain; inflation means to "_increase the monetory supply_". In the cosmos-hub-chain, it is its native token "ATOM" that acts as a monetory element. Inflation here means ATOM generation rate on annual basis. 

- If the inflaion rate is 7%; it means that tokens are generated at a 7% annual rate based off of the total supply of atoms.

- In cosmos-hub-chain all the inflated supply gets paid to all those actors who are stakers ( Validators and delegators ). 



## What controls the inflation
To understand the dynamics and protocol enforced regulation; you need to understand a few concepts and terminology. So you can understand each factors or variables. 

cosmos-hub-chain is a proof of stake chain. Its live operations is run by a set of validators node which also allows delegation facility. Delegation meaning that the indivisual token holders can bond/stake their tokens with he system via any of the validator. Tokens holders are free to choose validators of their choice.
cosmos-hub-chain is run by its community members of validators, delegators and atom holders. They could be called as network actors. And A sytem which is run and maintained by its believers, should pay fair and deterministic incentives for their contributions. The rules has to be written and automated. 

Contributions are in terms of running the infrastructure, and locking the monetory elements with the system. Locking the monitoring elements with the system means, to provide the fund reserve. 

The current value of the token amount locked in the system for its fund reserve is called staked-supply or bonded-supply, while the total token amount available in the system at any give time is called the total-supply. And the difference between the two is called unbonded-supply or unbonded-holdings. 

At any point of time in the chain, the amount of inflated tokens or generated tokens will be distributed to bond holders or accounts who have staked their holdings with the system. Bond holders are the guys who have staked their tokens with te system as validator or delegators. 



Work done incentives -> Gas Feess
Block production incentives -> Inflation
 

If staked-supply is less than 67%, inflation rate gradually increases, (What is the rate of increase though?) until that target is hit. If staked-supply is  greater 67%, it gradually decreases until it falls below that rate.

Inflation (supply increase) will range between 7% and 20%. That is calculated using the total number of atoms.

**Goal Percentage bond**

It is the balanced value of percentage bond.

**Current Percentage bond**
It is the current value of percentage bond in the system.

**Inflation Rate Upper limit**
20 % annual inflation rate.

**Inflation Rate Lower limit**
7 % annual inflation rate.

**Maximum Inflation Rate Change**
Maximum by which annual inflation rate can change in an year; it is set as 13%. 



**Inflation dynamics**

If the Current Percentage bond is below the goal percentage bonded value, then inflation rate will increase; untill the Inflation Rate Upper limit is reached. [ WHY? ] 

If the Current Percentage bond is greater than goal percentage bonded value, then inflation rate will decrease; untill the Inflation Rate Lower limit. [ WHY? ]  



Market Rate for Inflation Rewards 

Market Liquidity

Bonded Stake Ratio

Staked Supply

Total Supply

Total Bonded/Staked Value

**Annual Provisions**

**Block provisions** 
 Provision to be minted on each block production based on the current value of annual provision.
 
=====================================================================


On each block; system will be adjusted to reflect the current state of the blockchain. 
Inflation values will be recalculated based on the current state of the blockchain staking parameters. 







=====================================================================
Implementation Details :
https://docs.cosmos.network/v0.42/modules/mint/


type Minter struct {
	Inflation        sdk.Dec   // current annual inflation rate
	AnnualProvisions sdk.Dec   // current annual exptected provisions
}

type Params struct {
	MintDenom           string  // type of coin to mint
	InflationRateChange sdk.Dec // maximum annual change in inflation rate
	InflationMax        sdk.Dec // maximum inflation rate
	InflationMin        sdk.Dec // minimum inflation rate
	GoalBonded          sdk.Dec // goal of percent bonded atoms
	BlocksPerYear       uint64   // expected blocks per year
}

// NextInflationRate returns the new inflation rate for the next hour.

func (m Minter) NextInflationRate(params Params, bondedRatio sdk.Dec) sdk.Dec {
	// The target annual inflation rate is recalculated for each previsions cycle. The
	// inflation is also subject to a rate change (positive or negative) depending on
	// the distance from the desired ratio (67%). The maximum rate change possible is
	// defined to be 13% per year, however the annual inflation is capped as between
	// 7% and 20%.

	// (1 - bondedRatio/GoalBonded) * InflationRateChange
	inflationRateChangePerYear := sdk.OneDec().
		Sub(bondedRatio.Quo(params.GoalBonded)).
		Mul(params.InflationRateChange)
	inflationRateChange := inflationRateChangePerYear.Quo(sdk.NewDec(int64(params.BlocksPerYear)))

	// adjust the new annual inflation for this next cycle
	inflation := m.Inflation.Add(inflationRateChange) // note inflationRateChange may be negative
	if inflation.GT(params.InflationMax) {
		inflation = params.InflationMax
	}
	if inflation.LT(params.InflationMin) {
		inflation = params.InflationMin
	}

	return inflation
}
  
  NextAnnualProvisions(params Params, totalSupply sdk.Dec) (provisions sdk.Dec) {
	return Inflation * totalSupply
  }
  
========================================
BlockProvision(params Params) sdk.Coin {
	provisionAmt = AnnualProvisions/ params.BlocksPerYear
	return sdk.NewCoin(params.MintDenom, provisionAmt.Truncate())
  }
  
 
 
Calculate the provisions generated for each block based on current annual provisions. The provisions are then minted by the mint module's ModuleMinterAccount and then transferred to the auth's FeeCollector ModuleAccount.
================================================

Key	Type	Example
MintDenom	string	"uatom"
InflationRateChange	string (dec)	"0.130000000000000000"
InflationMax	string (dec)	"0.200000000000000000"
InflationMin	string (dec)	"0.070000000000000000"
GoalBonded	string (dec)	"0.670000000000000000"
BlocksPerYear	string (uint64)	"6311520"

================================================

**FAQ**

**Why the Goal Percentage Bond should be set less than 100% bonded?**
Because the remaining unbonded tokens can provide some liquidity. 
 
3. 


