# Verified by BLOCKS (VBB) - light verification pre and post mint example

----------------------------------------------------------------------------

## Pre-Mint Verification:

**Step 1:**
Your NFT metadata should add an additional “blocks_data” field which contains the transaction id of the Blocks transaction. The default metadata fields with verification would look like this:

```
{
  "name":"NFT Project Name",
  "image":"https://imageurl",
  "description":"This is an NFT.",
  "blocks_data":"" //Your BLOCKS verification transaction id will go here.
}
```

**Step 2:**
Create a SHA256 hash of your metadata.

Hash the metadata: ```'{"name":"NFT Project Name","image":"https://imageurl","description":"This is an NFT.","blocks_data":""}'```
Generated hash: ```A56B0605FBE06D189BEE6B8AB2917357731EE7DBFC703F49FD0872B399B8C4CE```

**Step 3:**
You will need to create the BLOCKS verification transaction before minting your NFT. This way you have the transaction id ready to place in the "blocks_data" field of your metadata. The BLOCKS transaction metadata is stringified json as follows:

```
'{
  "name":"NFT Project Name",
  "creator":"0xf0e3ea754D038b979CD0124e2f1A4Bf44f32746a", // Enter the full creator wallet address
  "hash":"A56B0605FBE06D189BEE6B8AB2917357731EE7DBFC703F49FD0872B399B8C4CE" //Enter the full SHA256 hash of the metadata
}'
```

**Step 4:**
Get the BLOCKS transaction id and insert it into your NFT metadata, then mint your NFT.

--------------------------------------------------------------------------------------

## Post-Mint Verification:
The NFT metadata does not contain the “blocks_data” field because it has already been minted. You can however fetch and hash the metadata retroactively.

**Step 1:**
Fetch your NFT metadata and create a SHA256 hash.

Hash this: ```'{"name":"NFT Project Name","image":"https://imageurl","description":"This is an NFT."}'```
Generated hash: ```D94D0234B3CA98C1657029D1919EC41B6D251026FAE57A81C5D9AE1A64562EC4```

**Step 2:**
Create the BLOCKS verification metadata. The BLOCKS transaction metadata is stringified json as follows:

```
'{
  "name":"NFT Project Name",
  "creator":"0xf0e3ea754D038b979CD0124e2f1A4Bf44f32746a", // Creator wallet address, address that minted the NFT
  "contract":"0x86fFdB8d83DC430E0576d498a389F474eefee8a7"//Contract address of your minted NFT
  "hash":"D94D0234B3CA98C1657029D1919EC41B6D251026FAE57A81C5D9AE1A64562EC4" //SHA256 hash of metadata
}'
```

**Step 3:**
Save the returned BLOCKS transaction id for future reference of verification.

## BLOCKS Data API

You can easily add the verification data on-chain using the BLOCKS Data API. This API facilitates multi-chain BLOCKS data transactions. Access the documentation [here](https://documenter.getpostman.com/view/3945331/UVypxwGn).

## Have Fun

Have fun exploring and building on BLOCKS with data transactions.


## License

Copyright © 2021 <BLOCKS DAO, LLC>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
