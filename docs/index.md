# Transaction

[index.js:48-303](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L48-L303 "Source code on GitHub")

Creates a new transaction object.

**Parameters**

-   `data` **Buffer or Array or Object** a transaction can be initiailized with either a buffer containing the RLP serialized transaction or an array of buffers relating to each of the tx Properties, listed in order below in the exmple.Or lastly an Object containing the Properties of the transaction like in the Usage example.For Object and Arrays each of the elements can either be a Buffer, a hex-prefixed (0x) String , Number, or an object with a toBuffer method such as Bignum
    -   `data.chainId` **Number** EIP 155 chainId - mainnet: 1, testnet: 3
    -   `data.nonce` **Buffer** nonce number
    -   `data.gasLimit` **Buffer** transaction gas limit
    -   `data.gasPrice` **Buffer** transaction gas price
    -   `data.to` **Buffer** to the to address
    -   `data.Txtype` **Buffer** Txtype (0x01 for normal, 0x06 for private)
    -   `data.data` **Buffer** this will contain the data of the message or the init of a contract
    -   `data.v` **Buffer** EC recovery ID
    -   `data.r` **Buffer** EC signature parameter
    -   `data.s` **Buffer** EC signature parameter
    -   `data.value` **Buffer** the amount of ether sent

**Properties**

-   `raw` **Buffer** The raw rlp encoded transaction

**Examples**

```javascript
var rawTx = {
  Txtype: '0x01',
  nonce: '0x00',
  gasPrice: '0x09184e72a000',
  gasLimit: '0x2710',
  to: '0x0000000000000000000000000000000000000000',
  value: '0x00',
  data: '0x7f7465737432000000000000000000000000000000000000000000000000000000600057',
  v: '0x1c',
  r: '0x5e1d3a76fbf824220eafc8c79ad578ad2b67d01b0c2425eb1f1347e8f50882ab',
  s: '0x5bd428537f05f9830e93792f90ea6a3e2d1ee84952dd96edbae9f658f831ab13'
};
var tx = new Transaction(rawTx);
```

## getBaseFee

[index.js:264-270](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L264-L270 "Source code on GitHub")

the minimum amount of gas the tx must have (DataFee + TxFee + Creation Fee)

Returns **BN** 

## getChainId

[index.js:182-184](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L182-L184 "Source code on GitHub")

returns chain ID

Returns **Buffer** 

## getDataFee

[index.js:251-258](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L251-L258 "Source code on GitHub")

The amount of gas paid for the data in this tx

Returns **BN** 

## getSenderAddress

[index.js:190-197](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L190-L197 "Source code on GitHub")

returns the sender's address

Returns **Buffer** 

## getSenderPublicKey

[index.js:203-208](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L203-L208 "Source code on GitHub")

returns the public key of the sender

Returns **Buffer** 

## getUpfrontCost

[index.js:276-280](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L276-L280 "Source code on GitHub")

the up front amount that an account must have for this transaction to be valid

Returns **BN** 

## hash

[index.js:150-176](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L150-L176 "Source code on GitHub")

Computes a sha3-256 hash of the serialized tx

**Parameters**

-   `includeSignature` **[Boolean]** whether or not to include the signature (optional, default `true`)

Returns **Buffer** 

## sign

[index.js:238-245](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L238-L245 "Source code on GitHub")

sign a transaction with a given private key

**Parameters**

-   `privateKey` **Buffer** 

## toCreationAddress

[index.js:141-143](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L141-L143 "Source code on GitHub")

If the tx's `to` is to the creation address

Returns **Boolean** 

## validate

[index.js:287-302](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L287-L302 "Source code on GitHub")

validates the signature and checks to see if it has enough gas

**Parameters**

-   `stringError` **[Boolean]** whether to return a string with a description of why the validation failed or return a Boolean (optional, default `false`)

Returns **Boolean or String** 

## verifySignature

[index.js:214-232](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L214-L232 "Source code on GitHub")

Determines if the signature is valid

Returns **Boolean** 

## from

[index.js:121-125](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L121-L125 "Source code on GitHub")

**Properties**

-   `from` **Buffer** (read only) sender address of this transaction, mathematically derived from other parameters.

## serialize

[index.js:114-114](https://github.com/WanJS/wanchainjs-tx/blob/8310148efaeaf5afc3163d71ca779d0737334ea3/index.js#L114-L114 "Source code on GitHub")

Returns the rlp encoding of the transaction

Returns **Buffer** 
