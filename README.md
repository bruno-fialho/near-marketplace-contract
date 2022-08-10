## NEAR Development 101

### AssemblyScript Contract Development

</br>

### How to interact with the contract:

</br>

1. Install CLI Tools

```
  yarn global add near-cli
  yarn global add assemblyscript
  yarn global add asbuild
```

2. Create a [Near testnet](https://wallet.testnet.near.org/) account

3. Login to the NEAR CLI:

```
  near login
```

4. Create a subaccount

```
  near create-account mycontract.myaccount.testnet --masterAccount myaccount.testnet --initialBalance 5
```

5. Compile the contract

```
  yarn asb
```

6. Deploy the contract

```
  near deploy --accountId=mycontract.myaccount.testnet --wasmFile=build/release/near-marketplace-contract.wasm
```

7. Call a change function

```
  near call mycontract.myaccount.testnet setProduct '{"id": "0", "productName": "tea"}' --accountId=myaccount.testnet

```

8. Call a view function

```
  near view mycontract.myaccount.testnet getProduct '{"id": "0"}'
```

- In order to call the buyProduct function:

9. Create a new subaccount

```
  near create-account buyeraccount.myaccount.testnet --masterAccount myaccount.testnet --initialBalance 6
```

10. Call buyProduct function

```
  near call mycontract.myaccount.testnet buyProduct '{"productId": "0"}' --depositYocto=1000000000000000000000000 --accountId=buyeraccount.myaccount.testnet
```

That's all!
