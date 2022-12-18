# Delegate Call

Delegate call and call are two very power full ways to call function or do transaction is Etherum but they have some important difference

- when we used `call` it mean execute the function on the call contract and update the value on that contract
- when we user `delegatecall` it will take that fucntiona and executr the contract which is call that function and used his storage mean

## Example one in contract

Contract B will set his values and used is storage varabiles
but when we call setValues function from contract A it will used it storage you can see traction and function execution but the values on Contract B will not update and any effect and when you check varaibale on contract A it will be set accotding to the index of variable on contract B without respect on the name.

## Example two

we are used proxy contract from openzeppelin
`It allow to look closely how delegate call is work in proxy. for that we user [!EIP-1967: Proxy Storage Slots](https://eips.ethereum.org/EIPS/eip-1967)
A consistent location where proxies store the address of the logic contract they delegate to, as well as other proxy-specific information.

We delopy contract small proxy and the implementation!A contract
the below line help us to used stroage to specifice point otherwise we used some storage point which used by something else

```
    // This is the keccak-256 hash of "eip1967.proxy.implementation" subtracted by 1
    bytes32 private constant _IMPLEMENTATION_SLOT =
        0x360894a13ba1a3210667c828492db98dca3e2076cc3735a920a3ca505d382bbc;
```

- `setImplementation`is take address of contarct which we want to implement or used as contract for delegate call so when we call any function which is implementation A contract then `small proxy ` first look in it if it will not found it them move to the delegate call for it copy function defination from there
- - `setImplementation ` and you change the implementatio then it point to new deployed contract.

- `getDataToTransact` is give you signature to call the function `setvalue` on small proxy contract
- `readStorage` will help you to read storage slot

but if we have some fucntion like `setImplementation` im implmentation contract there is no way you can call it that why we used tranprancy proxy method

# Thank you!

[![Touqeer Medium](https://img.shields.io/badge/Medium-000000?style=for-the-badge&logo=medium&logoColor=white)](https://medium.com/@touqeershah32)
[![Touqeer YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/channel/UC3oUDpfMOBefugPp4GADyUQ)
[![Touqeer Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/touqeer-shah/)
