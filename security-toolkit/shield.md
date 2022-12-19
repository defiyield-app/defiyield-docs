# Shield

DeFiYield's [**Shield**](https://defiyield.app/shield) is the best way to ensure that any assets in your wallet(s) are safe. This means we are always systematically scanning the smart contracts you have interacted with, any token contracts you are currently holding and any approvals you have granted to third-party contracts on any of our supported blockchains.

## Approval Checks

Through checking smart contracts you have interacted with, we are able to advise you on any outstanding approvals you have granted to any of them, and how much risk you are undertaking by having such tokens approved.

Approvals given to contracts that are possibly exploitable will be clearly marked and displayed in our **High Risk Contracts** section, along with a simple explanation of what the underlying issue is:

![](<../.gitbook/assets/image (5).png>)

Selecting **Revoke** on any past approval will allow you to quickly and easily set the approval to 0, disallowing the contract from transferring any tokens on your behalf:

![](<../.gitbook/assets/image (23).png>)

{% hint style="info" %}
Our [advanced mode](shield.md#advanced-mode) can aid you in more specifically setting desired approval amounts.
{% endhint %}

## ERC-20 Token Risks

By analyzing any tokens in your wallet(s), we highlight tokens that may be vulnerable to exploits on our **High Risk Tokens** section, present an explanation as to why that is the case, as well as how much exposure you have to any of these tokens:

![](<../.gitbook/assets/image (10) (1).png>)

Selecting **Swap** will allow you to easily and safely swap the vulnerable tokens out of your wallet.

## NFT Safety

Similarly to our contract approval checks, the Shield page will clearly denote any NFTs (ERC-721 or ERC-1155 contracts) in your wallet(s) with outstanding approvals to exchange, trading or marketplace contracts that have been detected as vulnerable for any reason displayed.

![](<../.gitbook/assets/image (43).png>)

Through the **Revoke** option, those approvals can also be easily nullified.

## Advanced Mode

While by default our interface will only display some of the most high risk security concerns, activating Advanced Mode enabled you to browse through different levels of issues identified by our Shield and take a deeper dive into securing your wallet's safety.

![Toggle advanced mode on the top right of the page.](<../.gitbook/assets/image (20).png>)

**High Risk** issues (shown in <mark style="color:red;">red</mark>) are usually exploitable vulnerabilities in any given contract which may require immediate attention.

**Medium Risk** issues (shown in <mark style="color:orange;">orange</mark>) can refer to non-vulnerability issues, but perhaps issues of an owner's control over a contract, or ways with which permissions may be used nefariously.

**Low Risk** issues (shown in <mark style="color:green;">green</mark>) refer to small points of concern among a specific contract, such as loss of precision on specific calculations, lack of events emitted during important transactions, etc.

**Informational** issues are anything else useful to denote, but with no particular emergency or vulnerability to patch. These can be issues such as outdated solidity versions, sub-standard code or usage of some particularly unreliable functions.

![](<../.gitbook/assets/image (35).png>)

You may also choose to filter through issues, in order to only disclose vulnerabilities you are personally concerned with:

![](<../.gitbook/assets/image (26).png>)

With advanced mode enabled, you will also have the option to alter any token approval rather than outright revoking it. This is particularly useful in other to curb unlimited allowances you have set in the past:

![](<../.gitbook/assets/image (12).png>)
