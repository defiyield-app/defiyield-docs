# Scanner

{% hint style="warning" %}
Our smart contract scanner is still under development. Keep an eye out a full release coming soon!
{% endhint %}

DeFiYield's smart contract scanner can be used to quickly gather a comprehensive analysis of any smart contract on our supported chains. This is to ensure that the contracts you plan on interacting with are safe, without having to rely on often misleading audits that most often lack proper coverage.

## Our Features

#### Expansive Vulnerability Coverage

The scanner doesn't only scan for the most superficial exploits and threats like reentrancy attacks, unchecked transfers, etc. Any exploit or vulnerability discovered in the recent years has been included and are checked for. This includes anything from Solidity best practices to ERC standards, proper control flow or checking proper privileged function setups.

#### Simple & Informative Security Score

Our scanner generates a simple security score to quickly infer the riskiness of any given contract.

![](<../.gitbook/assets/Scanner Score.jpg>)

#### Detailed Reports

Alongside the security score, our scanner provides you with a PDF report of all its findings, alongside a similarity report. This means you'll know exactly what made up its score, what the contract's issues are and how to fix them, as well as how similar the contract is to any other contracts deployed elsewhere, including many known scam contracts.

#### Fast Scanning

In less than a couple seconds you are able to have all the details regarding any contract you'd like, with likely better coverage than most audits out there.

## Scanner Architecture

![](<../.gitbook/assets/Scanner Structure.png>)
