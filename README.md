# GraceVault Smart Contract

A Clarity smart contract for creating and managing time-locked vaults with beneficiary claims and owner ping mechanism.

## Overview

GraceVault enables users to create time-locked vaults that can be claimed by designated beneficiaries after specific conditions are met. The contract includes safety features like owner pings to prevent premature claims and administrative controls.

## Features

- Create time-locked vaults with specified beneficiaries
- Owner ping mechanism to maintain vault activity
- Beneficiary claim system with time-lock verification
- Vault cancellation by owners
- Administrative controls
- View functions for vault data

## Functions

### Admin Functions
- `set-admin`: Update contract administrator

### Vault Functions
- `create-vault`: Create a new time-locked vault
- `ping`: Update vault activity status
- `claim`: Claim vault contents as beneficiary
- `cancel-vault`: Cancel and delete a vault
- `get-vault`: View vault details

## Error Codes

| Code | Description |
|------|-------------|
| 100  | Unauthorized access |
| 101  | Vault not found |
| 102  | Vault is locked |
| 103  | Vault already claimed |
| 104  | Not the beneficiary |
| 105  | Not the vault owner |
| 106  | Ping too early |

## Usage

```clarity
;; Create a new vault
(contract-call? .gracevault create-vault 
    'BENEFICIARY-ADDRESS 
    u1000000 ;; amount in micro units
    u100     ;; unlock block height
)

;; Ping a vault
(contract-call? .gracevault ping u1)

;; Claim a vault
(contract-call? .gracevault claim u1)
```

## Security Considerations

- All functions include proper authorization checks
- Time-locks are enforced through block height verification
- Owner pings prevent unauthorized claims
- Amount validation prevents zero-value vaults


## License

MIT License
