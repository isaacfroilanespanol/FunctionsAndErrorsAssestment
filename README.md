Introduction
This Solidity smart contract implements a decentralized crowdfunding platform. Campaign creators can create fundraising campaigns with specific goals and deadlines. Contributors can fund these campaigns, and once the goal is reached, the campaign creator can withdraw the funds.
Features
* Campaign Creation: Create campaigns with specified funding goals and deadlines.
* Contributions: Contribute ETH to active campaigns.
* Fund Withdrawal: Campaign creators can withdraw funds if the goal is met by the deadline.
* Assertions: Ensure that the campaign exists using Solidity's assert statement.
Smart Contract Functions
createCampaign(uint _goal, uint _deadline)
Creates a new crowdfunding campaign.
* _goal: The funding goal for the campaign (in wei).
* _deadline: The Unix timestamp for the campaign deadline.
Requirements:
* The goal must be greater than zero.
* The deadline must be in the future.
Events:
* CampaignCreated(uint campaignId, address creator, uint goal, uint deadline)
contribute(uint _campaignId)
Allows users to contribute funds to a specified campaign.
* _campaignId: The ID of the campaign to contribute to.
Requirements:
* The campaign must exist.
* The current timestamp must be before the campaign's deadline.
* The contribution amount must be greater than zero.
Events:
* ContributionMade(uint campaignId, address contributor, uint amount)
* CampaignFunded(uint campaignId, uint totalFunds): Triggered when the campaign reaches its funding goal.
withdrawFunds(uint _campaignId)
Allows the campaign creator to withdraw funds if the campaign goal is met.
* _campaignId: The ID of the campaign to withdraw funds from.
Requirements:
* The campaign must exist.
* Only the campaign creator can withdraw funds.
* The current timestamp must be after the campaign's deadline.
* The campaign goal must have been reached.
Reverts:
* If the campaign goal was not reached.
assertCampaignExists(uint _campaignId)
Asserts that a campaign exists.
* _campaignId: The ID of the campaign to check.
Assertions:
* The campaign ID must be valid (less than campaignCount).
Events
* CampaignCreated(uint campaignId, address creator, uint goal, uint deadline): Emitted when a campaign is created.
* ContributionMade(uint campaignId, address contributor, uint amount): Emitted when a contribution is made.
* CampaignFunded(uint campaignId, uint totalFunds): Emitted when a campaign reaches its funding goal.
Usage
1. Deploy the Contract:
    * Deploy the Crowdfunding contract using a Solidity-compatible environment like Remix or Truffle.
2. Create a Campaign:
    * Call the createCampaign function with the desired goal and deadline.
3. Contribute to a Campaign:
    * Call the contribute function with the campaign ID and send ETH along with the transaction.
4. Withdraw Funds:
    * After the campaign's deadline, the creator can call the withdrawFunds function to withdraw the raised funds if the goal was met.
5. Check Campaign Existence:
    * Use the assertCampaignExists function to ensure a campaign exists before interacting with it.
Example Usage in Remix
1. Deploy the Contract:
    * Copy the contract code into Remix.
    * Select the appropriate compiler version and compile the contract.
    * Deploy the contract using the "Deploy" button.
2. Create a Campaign:
    * Call createCampaign with parameters like 1000000000000000000 (1 ETH) for _goal and a future timestamp for _deadline.
3. Contribute to a Campaign:
    * Call contribute with the campaign ID and send ETH using the value field in Remix.
4. Withdraw Funds:
    * Call withdrawFunds with the campaign ID after the deadline if the goal was reached.
5. Check Campaign Existence:
    * Call assertCampaignExists with the campaign ID to verify its existence.
  
License
This project is licensed under the MIT License.

