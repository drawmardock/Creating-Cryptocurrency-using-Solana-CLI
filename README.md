# Creating-Cryptocurrency-using-Solana-CLI

First up, you need to have a functioning rust installation along with cargo.

curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

we need to install the Solana tool suite in our machine. To do so, run the following command.

sh -c "$(curl -sSfL https://release.solana.com/v1.7.12/install)"

To confirm that Solana has been installed successfully and added to your PATH, run

solana --version

Now, we’ll be installing the spl-token-cli for creating our tokens

cargo install spl-token-cli

Creating a wallet and check the balance 
solana-keygen new

You can  verify your balance  by pasting your public key on the solana explorer - https://explorer.solana.com/?cluster=devnet

of course the result will be 0 SOL

let's add some devnet money on our wallet 
solana airdrop 2 <public key> --url https://api.devnet.solana.com
  
  
 check your new balance
  solana balance <public key> --url https://api.devnet.solana.com
  Result: 2 SOL
  
 Creating your own tokens
  spl-token create-token
  
  Result: <token address>
  
  
  create an account for us in our wallet and verify token balace
  
 Create account
  spl-token create-account <token address> --url https://api.devnet.solana.com
 Token balance 
  spl-token balance <token address> --url https://api.devnet.solana.com
  
  Total Supply 1000 and Burning tokens 300 of them
    spl-token supply <token address>
  Example: spl-token 1000 <token address> --url https://api.devnet.solana.com
  Result/output: 1000
  
  spl-token burn <source token account address> <tokens to be burnt>
  Example : spl-token burn <source token account address> 300 --url https://api.devnet.solana.com
  Result/output: 700
  
  Send to some friends and family 
  Phantom wallet 
  add an account for your token in their wallet 
  spl-token transfer <your token account address> <total amount> <receiver’s wallet address>
  
  Name your Tokens
  pull request to the solana-labs/token-list: The community maintained Solana token registry repository
  
  Add an entry to the “solana.tokenlist.json” 
  {
   "chainId":101,
   "address":"your token address",
   "symbol":"your token symbol",
   "name":"Token Name",
   "decimals":"<number of decimals your token supports>",
   "logoURI":"the CDN link to your token's image",
   "tags":[
      "tags_if_any"
   ],
   "extensions":{

   }
}
  
  Once the pull request gets approved, you’ll be able to view the token image and name on every wallet in the Solana ecosystem.
