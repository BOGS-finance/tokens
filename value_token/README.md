# Value token

ERC20 token with a built-in intrinsic value, owner and central bank.

### Usage

Contructor:

    ValueToken(string _name, string _symbol, uint8 _decimals, uint256 _initialSupply, uint256 _initialValue, address _centralBank)
    
Mint / burn tokens:

    mint(uint256 _amount)
    burn(uint256 _amount)

Update value:

    updateValue(uint256 _newValue)
    updateValueAndMint(uint256 _newValue, uint256 _toMint)
    updateValueAndBurn(uint256 _newValue, uint256 _toBurn)

Transfer ownership and central banking:

    transferOwnership(address _newOwner)
    transferCentralBanking(address _newCentralBank)

### Owner vs central bank

The **owner** of the token controls ownership and central banking addresses.

The **central bank** can change the token value and mint or burn tokens BUT these tokens are modified on the **owner**'s balance.

This separation of concerns means that if the central bank is compromised, no damage can be achieved by a bad guy controlling it (he can only impact tokens on the owner's balance). The legitimate owner can simply transfer central banking to a new address, and the new central bank can undo any damage by minting or burning tokens as appropriate.

The owner however is not protected by the central bank and should therefore be stored securely.