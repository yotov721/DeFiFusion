**THIS CHECKLIST IS NOT COMPLETE**. Use `--show-ignored-findings` to show all the results.
Summary
 - [divide-before-multiply](#divide-before-multiply) (9 results) (Medium)
 - [reentrancy-no-eth](#reentrancy-no-eth) (1 results) (Medium)
 - [reentrancy-benign](#reentrancy-benign) (2 results) (Low)
 - [reentrancy-events](#reentrancy-events) (3 results) (Low)
 - [timestamp](#timestamp) (2 results) (Low)
 - [assembly](#assembly) (4 results) (Informational)
 - [pragma](#pragma) (1 results) (Informational)
 - [solc-version](#solc-version) (22 results) (Informational)
 - [low-level-calls](#low-level-calls) (4 results) (Informational)
 - [naming-convention](#naming-convention) (5 results) (Informational)
 - [immutable-states](#immutable-states) (5 results) (Optimization)
## divide-before-multiply
Impact: Medium
Confidence: Medium
 - [ ] ID-0
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse *= 2 - denominator * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L120)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-1
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [prod0 = prod0 / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L104)
	- [result = prod0 * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L131)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-2
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse *= 2 - denominator * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L122)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-3
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse *= 2 - denominator * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L125)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-4
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse *= 2 - denominator * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L124)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-5
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse *= 2 - denominator * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L123)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-6
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse *= 2 - denominator * inverse](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L121)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-7
[FusionStaking.calculateReward(uint256)](contracts/FusionStaking.sol#L191-L210) performs a multiplication on the result of a division:
	- [stakingDurationInDays = stakingDuration.div(86400)](contracts/FusionStaking.sol#L205)
	- [reward = stake.amount.mul(stakingDurationInDays).mul(rewardRateInPercentage).div(100).div(maxStakingDuration)](contracts/FusionStaking.sol#L207)

contracts/FusionStaking.sol#L191-L210


 - [ ] ID-8
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) performs a multiplication on the result of a division:
	- [denominator = denominator / twos](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L101)
	- [inverse = (3 * denominator) ^ 2](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L116)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


## reentrancy-no-eth
Impact: Medium
Confidence: Medium
 - [ ] ID-9
Reentrancy in [FusionStaking.stakeTokens(uint256)](contracts/FusionStaking.sol#L93-L118):
	External calls:
	- [! token.transferFrom(msg.sender,address(this),_amount)](contracts/FusionStaking.sol#L112)
	State variables written after the call(s):
	- [tokenIdCounter ++](contracts/FusionStaking.sol#L117)
	[FusionNFT.tokenIdCounter](contracts/FusionNFT.sol#L8) can be used in cross function reentrancies:
	- [FusionNFT.constructor()](contracts/FusionNFT.sol#L10-L12)
	- [FusionStaking.stakeTokens(uint256)](contracts/FusionStaking.sol#L93-L118)
	- [FusionNFT.tokenIdCounter](contracts/FusionNFT.sol#L8)

contracts/FusionStaking.sol#L93-L118


## reentrancy-benign
Impact: Low
Confidence: Medium
 - [ ] ID-10
Reentrancy in [FusionStaking.depositYield(uint256)](contracts/FusionStaking.sol#L175-L184):
	External calls:
	- [! token.transferFrom(owner(),address(this),_amount)](contracts/FusionStaking.sol#L179)
	State variables written after the call(s):
	- [totalYield += _amount](contracts/FusionStaking.sol#L182)

contracts/FusionStaking.sol#L175-L184


 - [ ] ID-11
Reentrancy in [FusionStaking.unstake(uint256)](contracts/FusionStaking.sol#L124-L169):
	External calls:
	- [require(bool,string)(token.transfer(msg.sender,withdrawAmount),Unstake failed)](contracts/FusionStaking.sol#L162)
	State variables written after the call(s):
	- [hasWithdrawn[msg.sender] = true](contracts/FusionStaking.sol#L168)

contracts/FusionStaking.sol#L124-L169


## reentrancy-events
Impact: Low
Confidence: Medium
 - [ ] ID-12
Reentrancy in [FusionStaking.stakeTokens(uint256)](contracts/FusionStaking.sol#L93-L118):
	External calls:
	- [! token.transferFrom(msg.sender,address(this),_amount)](contracts/FusionStaking.sol#L112)
	Event emitted after the call(s):
	- [Staked(msg.sender,_amount,tokenIdCounter)](contracts/FusionStaking.sol#L115)

contracts/FusionStaking.sol#L93-L118


 - [ ] ID-13
Reentrancy in [FusionStaking.unstake(uint256)](contracts/FusionStaking.sol#L124-L169):
	External calls:
	- [require(bool,string)(token.transfer(msg.sender,withdrawAmount),Unstake failed)](contracts/FusionStaking.sol#L162)
	Event emitted after the call(s):
	- [RewardClaimed(msg.sender,_tokenId,reward)](contracts/FusionStaking.sol#L165)
	- [Unstaked(msg.sender,_amount,_tokenId)](contracts/FusionStaking.sol#L164)

contracts/FusionStaking.sol#L124-L169


 - [ ] ID-14
Reentrancy in [FusionStaking.depositYield(uint256)](contracts/FusionStaking.sol#L175-L184):
	External calls:
	- [! token.transferFrom(owner(),address(this),_amount)](contracts/FusionStaking.sol#L179)
	Event emitted after the call(s):
	- [YieldDeposited(_amount)](contracts/FusionStaking.sol#L183)

contracts/FusionStaking.sol#L175-L184


## timestamp
Impact: Low
Confidence: Medium
 - [ ] ID-15
[FusionStaking.calculateReward(uint256)](contracts/FusionStaking.sol#L191-L210) uses timestamp for comparisons
	Dangerous comparisons:
	- [stakingDuration > maxStakingDuration](contracts/FusionStaking.sol#L198)

contracts/FusionStaking.sol#L191-L210


 - [ ] ID-16
[FusionStaking.unstake(uint256)](contracts/FusionStaking.sol#L124-L169) uses timestamp for comparisons
	Dangerous comparisons:
	- [reward > 0](contracts/FusionStaking.sol#L143)
	- [require(bool,string)(token.transfer(msg.sender,withdrawAmount),Unstake failed)](contracts/FusionStaking.sol#L162)

contracts/FusionStaking.sol#L124-L169


## assembly
Impact: Informational
Confidence: High
 - [ ] ID-17
[ERC721._checkOnERC721Received(address,address,uint256,bytes)](node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L399-L421) uses assembly
	- [INLINE ASM](node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L413-L415)

node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L399-L421


 - [ ] ID-18
[Math.mulDiv(uint256,uint256,uint256)](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134) uses assembly
	- [INLINE ASM](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L62-L66)
	- [INLINE ASM](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L85-L92)
	- [INLINE ASM](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L99-L108)

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L55-L134


 - [ ] ID-19
[Strings.toString(uint256)](node_modules/@openzeppelin/contracts/utils/Strings.sol#L19-L39) uses assembly
	- [INLINE ASM](node_modules/@openzeppelin/contracts/utils/Strings.sol#L25-L27)
	- [INLINE ASM](node_modules/@openzeppelin/contracts/utils/Strings.sol#L31-L33)

node_modules/@openzeppelin/contracts/utils/Strings.sol#L19-L39


 - [ ] ID-20
[Address._revert(bytes,string)](node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243) uses assembly
	- [INLINE ASM](node_modules/@openzeppelin/contracts/utils/Address.sol#L236-L239)

node_modules/@openzeppelin/contracts/utils/Address.sol#L231-L243


## pragma
Impact: Informational
Confidence: High
 - [ ] ID-21
Different versions of Solidity are used:
	- Version used: ['0.8.19', '^0.8.0', '^0.8.1']
	- [0.8.19](contracts/FusionNFT.sol#L2)
	- [0.8.19](contracts/FusionStaking.sol#L2)
	- [0.8.19](contracts/FusionToken.sol#L2)
	- [^0.8.0](node_modules/@openzeppelin/contracts/access/Ownable.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Enumerable.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/Context.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/Strings.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/math/SafeMath.sol#L4)
	- [^0.8.0](node_modules/@openzeppelin/contracts/utils/math/SignedMath.sol#L4)
	- [^0.8.1](node_modules/@openzeppelin/contracts/utils/Address.sol#L4)

contracts/FusionNFT.sol#L2


## solc-version
Impact: Informational
Confidence: High
 - [ ] ID-22
Pragma version[0.8.19](contracts/FusionStaking.sol#L2) necessitates a version too recent to be trusted. Consider deploying with 0.8.18.

contracts/FusionStaking.sol#L2


 - [ ] ID-23
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC20/extensions/IERC20Metadata.sol#L4


 - [ ] ID-24
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/math/Math.sol#L4


 - [ ] ID-25
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/Context.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/Context.sol#L4


 - [ ] ID-26
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/Strings.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/Strings.sol#L4


 - [ ] ID-27
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC721/IERC721Receiver.sol#L4


 - [ ] ID-28
Pragma version[^0.8.1](node_modules/@openzeppelin/contracts/utils/Address.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/Address.sol#L4


 - [ ] ID-29
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/math/SafeMath.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/math/SafeMath.sol#L4


 - [ ] ID-30
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Metadata.sol#L4


 - [ ] ID-31
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC20/IERC20.sol#L4


 - [ ] ID-32
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/introspection/ERC165.sol#L4


 - [ ] ID-33
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC20/ERC20.sol#L4


 - [ ] ID-34
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC721/extensions/ERC721Enumerable.sol#L4


 - [ ] ID-35
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/math/SignedMath.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/math/SignedMath.sol#L4


 - [ ] ID-36
Pragma version[0.8.19](contracts/FusionToken.sol#L2) necessitates a version too recent to be trusted. Consider deploying with 0.8.18.

contracts/FusionToken.sol#L2


 - [ ] ID-37
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC721/IERC721.sol#L4


 - [ ] ID-38
solc-0.8.19 is not recommended for deployment

 - [ ] ID-39
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Enumerable.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC721/extensions/IERC721Enumerable.sol#L4


 - [ ] ID-40
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/access/Ownable.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/access/Ownable.sol#L4


 - [ ] ID-41
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/utils/introspection/IERC165.sol#L4


 - [ ] ID-42
Pragma version[^0.8.0](node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4) allows old versions

node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L4


 - [ ] ID-43
Pragma version[0.8.19](contracts/FusionNFT.sol#L2) necessitates a version too recent to be trusted. Consider deploying with 0.8.18.

contracts/FusionNFT.sol#L2


## low-level-calls
Impact: Informational
Confidence: High
 - [ ] ID-44
Low level call in [Address.functionCallWithValue(address,bytes,uint256,string)](node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137):
	- [(success,returndata) = target.call{value: value}(data)](node_modules/@openzeppelin/contracts/utils/Address.sol#L135)

node_modules/@openzeppelin/contracts/utils/Address.sol#L128-L137


 - [ ] ID-45
Low level call in [Address.sendValue(address,uint256)](node_modules/@openzeppelin/contracts/utils/Address.sol#L64-L69):
	- [(success) = recipient.call{value: amount}()](node_modules/@openzeppelin/contracts/utils/Address.sol#L67)

node_modules/@openzeppelin/contracts/utils/Address.sol#L64-L69


 - [ ] ID-46
Low level call in [Address.functionStaticCall(address,bytes,string)](node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162):
	- [(success,returndata) = target.staticcall(data)](node_modules/@openzeppelin/contracts/utils/Address.sol#L160)

node_modules/@openzeppelin/contracts/utils/Address.sol#L155-L162


 - [ ] ID-47
Low level call in [Address.functionDelegateCall(address,bytes,string)](node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187):
	- [(success,returndata) = target.delegatecall(data)](node_modules/@openzeppelin/contracts/utils/Address.sol#L185)

node_modules/@openzeppelin/contracts/utils/Address.sol#L180-L187


## naming-convention
Impact: Informational
Confidence: High
 - [ ] ID-48
Parameter [FusionStaking.unstake(uint256)._tokenId](contracts/FusionStaking.sol#L124) is not in mixedCase

contracts/FusionStaking.sol#L124


 - [ ] ID-49
Parameter [FusionStaking.depositYield(uint256)._amount](contracts/FusionStaking.sol#L175) is not in mixedCase

contracts/FusionStaking.sol#L175


 - [ ] ID-50
Parameter [FusionStaking.calculateReward(uint256)._tokenId](contracts/FusionStaking.sol#L191) is not in mixedCase

contracts/FusionStaking.sol#L191


 - [ ] ID-51
Parameter [FusionStaking.stakeTokens(uint256)._amount](contracts/FusionStaking.sol#L93) is not in mixedCase

contracts/FusionStaking.sol#L93


 - [ ] ID-52
Function [ERC721.__unsafe_increaseBalance(address,uint256)](node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L463-L465) is not in mixedCase

node_modules/@openzeppelin/contracts/token/ERC721/ERC721.sol#L463-L465


## immutable-states
Impact: Optimization
Confidence: High
 - [ ] ID-53
[FusionStaking.rewardRateInPercentage](contracts/FusionStaking.sol#L28) should be immutable 

contracts/FusionStaking.sol#L28


 - [ ] ID-54
[FusionStaking.maxUserStake](contracts/FusionStaking.sol#L21) should be immutable 

contracts/FusionStaking.sol#L21


 - [ ] ID-55
[FusionStaking.maxTotalStake](contracts/FusionStaking.sol#L20) should be immutable 

contracts/FusionStaking.sol#L20


 - [ ] ID-56
[FusionStaking.token](contracts/FusionStaking.sol#L19) should be immutable 

contracts/FusionStaking.sol#L19


 - [ ] ID-57
[FusionStaking.maxStakingDuration](contracts/FusionStaking.sol#L29) should be immutable 

contracts/FusionStaking.sol#L29


