
# Cosmos Inflation Dynamics

## What is Inflation?

- To understand the inflation dynamic in the cosmos-hub-chain; it is important to first understand the inflation in the blockchain space.
Inflation and Inflation rate are interchangeable words in this space. Inflation means to inflat; means to grow to make something larger.

- In any application specific blockchain; inflation means to "_increase the monetory supply_". In the cosmos-hub-chain, it is its native token "ATOM" that acts as a monetory element. Inflation here means ATOM generation rate on annual basis. 

- If the inflaion rate is 7%; it means that tokens are generated at a 7% annual rate based off of the total supply of atoms.

- In cosmos-hub-chain all the inflated supply gets paid to all those actors who are stakers ( Validators and delegators ). 



## Community 
To understand the dynamics and protocol enforced regulation; you need to understand a few concepts and terminology. So you can understand each factors or variables. 

cosmos-hub-chain is a proof of stake chain. Its live operations is run by a set of validators node which also allows delegation facility. Delegation meaning that the indivisual token holders can bond/stake their tokens with he system via any of the validator. Tokens holders are free to choose validators of their choice.
cosmos-hub-chain is run by its community members of validators, delegators and atom holders. They could be called as network actors. And A sytem which is run and maintained by its believers, should pay fair and deterministic incentives for their contributions. The rules has to be written and automated. 

Contributions are in terms of running the infrastructure, and locking the monetory elements with the system. Locking the monitoring elements with the system means, to provide the fund reserve. 

The current value of the token amount locked in the system for its fund reserve is called staked-supply or bonded-supply, while the total token amount available in the system at any give time is called the total-supply. And the difference between the two is called unbonded-supply or unbonded-holdings. 

At any point of time in the chain, the amount of inflated tokens or generated tokens will be distributed to bond holders or accounts who have staked their holdings with the system. Bond holders are the guys who have staked their tokens with the system as validator or delegators. 



## What should control the inflation?

Now we know, that the inflated supply of tokens will be incentivized to the bond holders. 

Consider the case of 100 bonds vs 10 bond; and 100 new token supply.

- If the bonded-supply is high then the inflated supply will be shared among bigger number of bonds. And every one would get a less amount as the number of share holders are large. It is like sharing 100 new tokens supply among 100 bonds so everybond would get a share of only 1 tokens. 

- If the bonded-supply is less then the inflated supply will be shared amoung less number of bonds. And every one would get a high amount as the number of share holders are less.  It is like sharing 100 new tokens supply among 10 bonds so everybond would get only 10 tokens. 

- I think; it is clear that in the case #1; bond holders will be less interested to be the part of the system As it does not give enough monetory benifits for its supportes and believers. It is an imbalanced situations. And the case #2 will attract users to join the system as bond holders.

- To make a good balance; If the system observe a high percentage of bonding ( case #1 )  then it should relatively disincetivize the bold holders. Meaning that it should reduce the incentives from its current incentives.  And the only way to do is to reduce the amount of new supply on the upcoming supply points.  It is to discourage impatient bond holders to loose patients. And only true believers to stay with the system. In this case system encorage non believers bond holders to leave the system. So the system adjust its inflation rate to go down. Similary, if the system observe a low percentage of bonding ( case #2 ) then it should relatetively incentivize the bond holders. Meaning that it increase the incentives from its current incentives. And the only way to do so; is to increase the amount of supply on the upcoming supply points. 

- In the above paragraph; meaning of supply point in the context of blockchain is newly produced blocks. Each block is a supply point. Supply of new generated tokens. 


 
## What happens in the cosmos-hub-chain?

- cosmos-hub-chain has set a goal for a balance point of bonded percentage, called GoalBonded. Bond percentage is simply the ratio of the current value of bonded atoms to the total supply at the moment of calculations. GoalBonded is the optimum value the system is trying to obtain with its dynamics. 

- Above and below this value the system is said to operate with a certain degree of imbalance. System dynamics is designed to obtain this value. 

- If the current value of the bond ratio is going far above; system tries to reduce the inflation rate based on how far it went.  The bigger the distance, bigger the rate of reduction in the inflation rate. The bigger the distance; lesser the value of inflation rate. And the value for the rate of reduction and the current value of inflation rate is dynamically calculated at each supply points. Meaning that system will adjust its rate of reduction in the inflation rate and also the current value of the inflation rate at each block production. 

- If the current value of the bond ratio is going far behind; system tries to increase the inflation rate based on how far it went behind the Goal. The bigger the distance, bigger the rate of increase in the inflation rate. The bigger the distance; bigger the value of inflation rate. And the value for the rate of increase and the current value of inflation rate is dynamically calculated at each supply points. Meaning that system will adjust its rate of increase in the inflation rate and also the current value of the inflation rate at each block production. 

## Limiting the Value of Inflation Rate 

- Similar to the cap on the current value of inflation rate change; The current value of inflation rate can not go up to any height or down to zero.

- This Inflation rate will always be greater than predetermined min value; and less than a predetermined max value. The Min value and Max value is a configurable parameter in the system. 



## Limiting the Value of Inflation Rate Change 
- Though the system can not have any big or less value of the inflation rate change for increasing or reduction of rate. Positive rate change reflect the increase in the value of inflation rate; while negative rate change reflect the reduction in the value of inflation rate. 

- System should set the maximum value of possible inflation rate change.  

- cosmos-hub-chain controls the positive max value of inflation rate change using a configurable parameter. 

- Negative max value is determined by the current value of the ratio relative to positive max.   

- The minimum absolute value of possible inflation rate change is zero. And it happens when the system is at its optimal value of bonded ratio.  At this point system will not change its inflation rate on its own.  


## Inflation tail dynamics 
- When the inflation is in its growing trend due to having the systems bonded ratio less than optimal value; inflation can reach to its max value and after that it just stops increasing. At this point if system tries to further increase its inflation rate change so it can give more incentives to bond holders by having more and more monetory supply;  it can not go further.  At this point Inflation rate change is set to zero by the protocol, and inflation is set to its max value. And the system just can not increase the collective incentives for its bonded users. Can not attract more by becoming more attractive. 

- When the inflation is in its downward trend due to having the systems bonded ratio greater than optimal value; inflation can reach to its min value and after that it just stops decreasing further. At this point if system tries to further decrease its inflation rate change so it can reduce the incentives to bond holders by having produced less and less monetory supply; it can not do so. At this point Inflation rate change is set to zero by the protocol, and inflation is set to its min value.  And the system just can not reduce the collective incentive for its bonded users. System can not be unfair more by trying to discourage non-believers. System can discourage the non-believers by upto this extent only. 

- But the system dynamics will again move the system to unbalanced zone. So it will again try to come back to balanced point. This is a never ending dynamics. I will explain this complexity in some other section. 


## Formula of current inflation rate change is given by;

```

   CurrentInflationRateChange = ( 1 - CurrentBondedRatio / GoalBondedRatio ) ) * MaxPositiveInflationRateChange
   Provided the CurrentInflationRate is in its defined range. [ You will see in the next section of Inflation Rate Limit ]    
   Otherwise Its value if set to zero. 
   
```


## Current value of the inflation rate

- Current value of the inflation rate is determined by its previous value and currrent value of Inflation Rate Change. 

- By now it is very clear that it is being recalculated at each supply point or block production.

- When the inflation is in its growing trend due to having the systems bonded ratio less than optimal value; inflation can reach to its max value and after that it just stops increasing.  

- When the inflation is in its downward trend due to having the systems bonded ratio greater than optimal value; inflation can reach to its min value and after that it just stops decreasing further. 


## Implementation
-> Inflation dynamics is implemented in the cosmos-sdk mint module.
-> https://docs.cosmos.network/v0.42/modules/mint/ 


## Inflation dynamics graph 

- https://drive.google.com/file/d/1qrYpTa3riBcemhojGJrHDE6sIzoKlUcP/view?usp=sharing 

- https://drive.google.com/file/d/1aD3WBzYvB6AKcTNp6cUIWdfZ0G048Hhw/view?usp=sharing

====================================================================================

# TODO 

## Effective Inflation Rate 
TODO 

## Can the True Inflation Rate be negative : 
I think so; When we are burning tokens it can go temporary negative for that particular block. 
TODO 


## Types of incentives 
Work done incentives -> Gas Feess
Block production incentives -> Inflation
 
## System Inflation Dynamic Control Paramters 
TODO 
If staked-supply is less than 67%, inflation rate gradually increases, (What is the rate of increase though?) until that target is hit. If staked-supply is  greater 67%, it gradually decreases until it falls below that rate.

Inflation (supply increase) will range between 7% and 20%. That is calculated using the total number of atoms.

**Inflation Rate Upper limit**
20 % annual inflation rate.

**Inflation Rate Lower limit**
7 % annual inflation rate.

**Maximum Inflation Rate Change**
Maximum by which annual inflation rate can change in an year; it is set as 13%. 

# Inflation dynamics Questions You should Ask?

- If the Current Percentage bond is below the goal percentage bonded value, then inflation rate will increase; untill the Inflation Rate Upper limit is reached. [ WHY? ] 

- If the Current Percentage bond is greater than goal percentage bonded value, then inflation rate will decrease; untill the Inflation Rate Lower limit. [ WHY? ]  

- Why the Goal Percentage Bond should be set less than 100% bonded?
Because the remaining unbonded tokens can provide some liquidity. 

- Why is there a min threshold on the value of inflation rate?


- Why is there a max threshold on the value of inflation rate?


- Why is there a max threshold on the value of inflation rate change?

- Can we call it bond pendulum?


## Settin up clear terminologies

- Market Rate for Inflation Rewards 

- Market Liquidity

- Bonded Stake Ratio

- Staked Supply

- Total Supply

- Total Bonded/Staked Value

- atom-holder 

- nonatom-holders 

- atom-holdings

- bonded-atom-holders

- nonbonded-atom-holders

- bonded-atom-behavior

- nonbonded-atom-behavior

- Exteral actors 

- Potential actors 


**Annual Provisions**

**Block provisions** 
 Provision to be minted on each block production based on the current value of annual provision.
 
=====================================================================

# Ref :
- Work in progress. 
- On each block; system will be adjusted to reflect the current state of the blockchain. System control variables are likely to change   to reflect upon the current state of the control variables. 
- Inflation values will be recalculated based on the current state of the blockchain staking parameters. 


[ Input Control Variables ] -> [ SYSTEM STATE ] -> [ Input Control Variables ] 







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
  
================================================
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

 

