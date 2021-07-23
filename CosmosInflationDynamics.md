
Mint / Inlfation Dynamics

Inflation Rate
Inflation refers to the monetary supply "inflating" aka growing larger. 

Atoms are generated based off of the total supply of atoms.

All of the inflation gets paid to those staking.

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

NextInflationRate(params Params, bondedRatio sdk.Dec) (inflation sdk.Dec) {
	inflationRateChangePerYear = (1 - bondedRatio/params.GoalBonded) * params.InflationRateChange
	inflationRateChange = inflationRateChangePerYear/blocksPerYr

	// increase the new annual inflation for this next cycle
	inflation += inflationRateChange
	if inflation > params.InflationMax {
		inflation = params.InflationMax
	}
	if inflation < params.InflationMin {
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


