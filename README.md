Land Registry Smart Contract
A simple smart contract for registering and managing land ownership on the Ethereum blockchain. This contract allows users to register land parcels, transfer ownership, and query land details in a decentralized and transparent manner.

Features
Register Land: Users can register land parcels by providing an ID, location, and area.
Transfer Ownership: Registered landowners can transfer ownership to another address.
Query Land Details: Retrieve information about registered land parcels.
Ownership Verification: Check if a land parcel is registered and view its ownership details.
Prerequisites
Solidity Version: ^0.8.0
Ethereum development tools like Remix, Truffle, or Hardhat.
Smart Contract Overview
Contract: LandRegistry
Structs
Land: Represents a land parcel with properties:
uint256 id: Unique identifier for the land.
string location: Description of the land's location.
uint256 area: Area of the land in square meters.
address owner: Ethereum address of the current owner.
bool registered: Status indicating if the land is registered.
Events
LandRegistered: Emitted when a new land parcel is registered.
Parameters: landId, location, area, owner
OwnershipTransferred: Emitted when ownership of a land parcel is transferred.
Parameters: landId, oldOwner, newOwner
Functions
registerLand(uint256 _id, string memory _location, uint256 _area)
Registers a new land parcel.

Requirements: The land with the given ID must not already be registered.
Emits: LandRegistered event.
transferOwnership(uint256 _id, address _newOwner)
Transfers ownership of a registered land parcel to a new owner.

Requirements: The caller must be the current owner of the land.
Emits: OwnershipTransferred event.
getLand(uint256 _id)
Returns the details of a registered land parcel.

Returns: id, location, area, owner, registered status.
isLandRegistered(uint256 _id)
Checks if a land parcel is registered.

Returns: true if the land is registered, false otherwise.
Example Usage
Register Land
solidity
Copy
Edit
// Register land with ID 1, location "Downtown", and area 500 sq. meters
landRegistry.registerLand(1, "Downtown", 500);
Transfer Ownership
solidity
Copy
Edit
// Transfer ownership of land with ID 1 to another address
landRegistry.transferOwnership(1, 0x1234...abcd);
Get Land Details
solidity
Copy
Edit
// Retrieve details of land with ID 1
(uint256 id, string memory location, uint256 area, address owner, bool registered) = landRegistry.getLand(1);
Deployment
Using Remix:

Open Remix IDE.
Create a new file LandRegistry.sol and paste the contract code.
Compile using the Solidity compiler version ^0.8.0.
Deploy the contract using the "Deploy & Run Transactions" tab.
Using Truffle/Hardhat:

Install Truffle or Hardhat.
Add the contract to your project and configure the deployment scripts.
Run truffle migrate or npx hardhat run scripts/deploy.js.
