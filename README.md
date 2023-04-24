# Deployment procedure

Admitting you've already set up starknet dev environment following the bootcamp first session, you can follow these steps to deploy a contract.

## Run python virtual environment

```source venv/bin/activate```

## Create a user account

```starknet new_account --account my_account```

The account is only declared on local see ```~/.starknet_accounts```
this command give us the address and public key. Now you should fund this account (because of account abstraction) before doing any further step.

## Deploy a user account

```starknet deploy_account --estimate_fee --account my_account```

Should output something like: "the estimated fee id 633263650817160 WEI (0.000633 ETH)"

Then take this gas fee and increase by 25% to make sure it's enough:

```starknet deploy_account max_fee 933263650817160 --account my_account```

Now the account is on-chain and deployed.

## Declare with this account 

Before deploying a smart contract it must be declared.

```starknet declare --contract sierra/example.json --account v0.01_b``` 

This could give an error with the class hash displayed if it's already declared, copy the class hash.

## Deploy contract to testnet

```starknet deploy --class_hash my_hash --account my_account```
