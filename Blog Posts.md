<h1>POST 1</h1>

<h2>What is blockchain?</h2>
Blockchain is essentially a datastore, it is a very safe datastore.Its public, its just like a database
There are only 2 things you can do with it:

1) write to it  
2) read from it

<h2>How to write to it?</h2>

You come up with a transaction of something that has to be written to a blockchain,and you are going to send it to the distributed system or the blockchain. It goes over there and all of the info is collected together and put together in whats called a “Block” , inside a block they are put in to smaller “package”. And this package is sent to what is called a “Verifier”.So these verifiers look at the content of the transactions in this one block ,all of them. And they are going to ensure that they satisfy the rules defined by the blockchain.

![image](https://user-images.githubusercontent.com/62566404/159703272-8c54ab59-cd08-40b8-a77e-c9b808d6797e.png)


For instance if we are talking about currency we confirm that the sender has the amount he is sending to confirm the transaction, rules like that, verifiers verify everything. After verification, verifiers send this “signed or confirmed” information back to the blockchain or the “greater network”.That is essentially a Blockchain.

Just like that there will be some other blocks and they will be connected to each other through a chain so on and so forth.They will be linked together throught a series of operations.In essence this is what a blockchain is. You keep on adding to the blockchain and this keeps on growing and is available publicly to everyone. That is what a public blockchain is. At each given instance we need to confirm that transactions are actually being made and all the rules are being followed. That is job of all the different verifiers, that keep the blockchain running


Obviously there is alot more to it.

<h2>Wallet:</h2>
Think of the wallet as your “identifier” it has two parts: 


```mermaid
graph TD;
   Wallet-->PublicKey;
   Wallet-->PrivateKey;   
```

1)A public key 

2)A private key


<h3>A public key:</h3> Is what you share with everyone hence the name “Public” and everyone can identify you via that. Whenever you say that for example  a wallet “1234x567890x1011” is completing a transaction  we actually mean that a person who owns this wallet is completing a transaction.We are going to take a look at them later. 
<h3>A private key:</h3> Associated with each public key is a thing called “private key” .what a private key does is it puts signatures on all the transactions.Think of it this way we need public key to actually sign into the blockchain, once we sign in people would be able to see it using your public. But they cannot sign stuff on your behalf.The thing to note is that only you can do the signature using the private key. YOU DO NOT share it with anyone, hence you can write/sign but everyone can verify. Obviously this is just the skim of it however what you really to need to know is the your Private key should be left PRIVATE and your public key PUBLIC.

<h2>How to create Private and Public Keys:</h2>

We can create these keys through a variety of ways and via a lot of tools but for this specific blog we are going to use a wallet.  A wallet is essentially what allows you to take care of your private and public keys. There are alot of E-wallets out there but again for this specific blog we are going to use a popular one called “Metamask” .Ethereum has a list of suggested wallets and this is one of them. We need this whole setup of the blockchain on our local machine and the local system would be called a node. Think of it as the mirror of the actual blockchain you are going to be working with. Inorder to create this local node, there are plenty of tutorials that allow you to build this thing from scratch, but think of it in this way like you dont build your own webservers to start a website , you use apache etc.(layman) We are going to be using a framework called hardhat. It is a very popular tool to create local blockchain, then we are going  to move on to a distributed global network which is going to be the Ropsten test ,that is going to be exactly a mirror of the ethereum blockchain. And all the real life ethereum smart contracts and everything live on it is same as the actual live blockchain.It is the mirror of the mainet. It allows you to use fake currency before going to real working currency and actually deploying it on the mainet. We will not include that part unfortunately in this tutorial because that would require use of real ethereum. Once you get to the real ropsten testnet the ethereum mainnet  is literally the same thing. You just have to change a couple of URLS here and there and Boom you good to go. Essentially this is all you worry about. 

![image](https://user-images.githubusercontent.com/62566404/159703636-02af4041-c65f-4418-9133-70d8045953b5.png)

<h2>GAS:</h2>



When you're going to write to the blockchain you need something which is called “Gas”, It is mandatory inorder to write something to the blockchain. And you're going to need it for your first transaction. There are a couple of third party resources that give you the “money to play with “ on the testnet. Disclaimer this is fake money so you can't really use it to buy video games, we mean "project resources".//so we are going use faucet to it some gas// finally when we are going to read some information of the blockchain, we are going to use node js application that is going to go and read the information for us, for this we are going to use the popular library called ether to communicate with the blockchain.You may have realized that we have not dug deep into the usual topics such as what blocks, hashes etc are. And the reason is that you dont need to know all of that inorder to create a blockchain and to use it.That is one of the biggest problems that make other blogs  BORING and lengthy. You dont need to know how the engine works inorder to drive a car, just like in this case you dont need to know about the hashes and the blocks to run a blockchain. Dont take my word for it, just headover to the ethereum guy’s(Gavin Wood) solidarity official documentation.(solidarity: official language for ethereum blockchain).
Sheeesh that was long.To summarize what we would be doing in this blog is that:

1)Make a simple Node js application 

2)Connect it to the blockchain

3)Using metamask we are going to create public private keys

4)We are going to create a node with hardhat, which is going to put everything come together.


** “So letssssss get it STARTED in here” **

<h1>POST 2</h1>

<h2>Environment Setup</h2>
Here's the stuff we'll need
<ul>
<li>Linux Operating System(preferrably)</li>
<li>NVM</li>
<li>Node</li>
<li>Hardhat</li>
<li>MetaMask Wallet</li>
</ul>
Press(in linux) Alt-F2 to open the Run Command box
Set up NVM first for

``` curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash ```

Add the environment variables for accessing node commands.
``` nvm install --lts ```
![image](https://user-images.githubusercontent.com/80161973/159760533-741adf75-cdcf-4aaa-8c94-408d3d737486.png)

![image](https://user-images.githubusercontent.com/80161973/159760649-3016b05d-0aa3-46e4-afcf-8c5ea801de6a.png)

![image](https://user-images.githubusercontent.com/80161973/159760692-906313ad-736c-4a2b-96f1-dcebb6f86b50.png)


<h2>Install MetaMask</h2>
MetaMask will manage our wallet so that we can easily view our accounts and test our DApps easily. Go ahead and install MetaMask from https://metamask.io/. I'll use Firefox but you can just as well use Chrome.
(I strongly suggest you use MetaMask for this tutorial so that you can follow along. There's a million wallets out there and it would be difficult to debug issues if you use something other than MetaMask.)
Just go ahead and create an account on MetaMask, set your password and then save the recovery keys as given in the instructions.

![image](https://user-images.githubusercontent.com/80161973/159760874-ceb9b874-d25e-4279-adab-c17cc2cb2049.png)

![image](https://user-images.githubusercontent.com/80161973/159760910-362125eb-de81-459e-84fe-ff63b82e723c.png)

![image](https://user-images.githubusercontent.com/80161973/159760934-837cc2e8-fb6d-4476-9467-38038fb848f6.png)


<h2>Setting up Hard hat</h2>
In order to test out our smart contracts, we need an environment that simulates the ethereum network locally. We will later try out our smart contract on a global testnet too.
First, set up a react app that we will use to interact with our environment.

```
 npx create-react-app react-dapp
cd react-dapp
```

Now go ahead and set up hardhat along with all its dependencies. For now, let's not go into the details of what each part does and what alternatives are available. That would only slow you down and create confusion. It's best to get a hello world done and study options afterwards.

```
npm install ethers hardhat @nomiclabs/hardhat-waffle \
            ethereum-waffle chai \
            @nomiclabs/hardhat-ethers
 ```
Let's create basic hardhat configs and setup.

```npx hardhat```

Accept all defaults. This will create a basic sample project for us.
We need to edit the hardhat config file so that this works well with MetaMask. ChainId is a unique identifier for the blockchain.

```vi hardhat.config.js```
```
module.exports = {
  solidity: "0.8.4",
  paths: {                         // add this 
    artifacts: './src/artifacts',  // this is where our compiled contracts will go
  },
  networks: {                      // and this ... 
    hardhat: {
      chainId: 1337                // this is needed for MetaMask
    }
  }
};
```
Start a node using:
```npx hardhat node ```
![image](https://user-images.githubusercontent.com/80161973/159761649-1726ce95-9702-4b3a-a4b8-b01b3123431a.png)

![image](https://user-images.githubusercontent.com/80161973/159761671-aa3e5516-a7b6-4fba-927f-55cd284c0f3e.png)

![image](https://user-images.githubusercontent.com/80161973/159761687-dcef6834-9a94-41a3-b6c9-9ec76fce2b22.png)

![image](https://user-images.githubusercontent.com/80161973/159761704-ea03d5ac-3631-4cfa-a5da-3a805b8ce323.png)

![image](https://user-images.githubusercontent.com/80161973/159761716-19b94225-c85c-4478-abef-5aedcc2bbfa9.png)

And try to connect to it using MetaMask.

![image](https://user-images.githubusercontent.com/80161973/159761737-2f4ea998-a60a-42ee-b10a-4bd93586b125.png)

<h1>POST 3</h1>


<h2>Smart Contract</h2>

Once we have the environment set up, we actually need to create a basic contract. The "hello world" for DApps is a greeter contract that does both reading and writing to the chain.
```
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;
```

```import "hardhat/console.sol";```

```contract Greeter {
   string greeting;


  constructor(string memory _greeting) {
    console.log("Deploying a Greeter with greeting:", _greeting);
    greeting = _greeting;
 }

  function greet() public view returns (string memory) {
return greeting;
  }

  function setGreeting(string memory _greeting) public {
    console.log("Changing greeting from '%s' to '%s'", greeting, _greeting);
   greeting = _greeting;
 }
}
   ```
 Our contract is in solidity. This cannot be accessed directly from our Javascript frameworks. For that, we need to "compile" it to Javscript (ABI). Think of this as a wrapper that connects to the contract and can help you call functions of the contract without having to worry about the details (marshalling etc.) yourself.
The actual command is pretty simple:

```npx hardhat compile```

A new file will be created in:
```src/artifacts/contracts/Greeter.sol/Greeter.json```

![image](https://user-images.githubusercontent.com/62806277/159704325-3b415914-201b-4316-a678-9f85b2ef05ea.png)

```We will import this file when writing our react script.```

 
 
![image](https://user-images.githubusercontent.com/62806277/159704344-55b7d75b-1192-4b29-a49d-7acc958ce3c1.png)

 
![image](https://user-images.githubusercontent.com/62806277/159704354-d1e821a0-c0b9-43b5-8648-7e792d4a120e.png)

 
 
 
 
<h3> Starting a Dummy Network and Deploying the Contract </h3>

```npx hardhat node```

<h3>Circumspection : </h3>

1. These are test accounts created for the purpose of testing the local network. We'll use these for a while. Make sure you don't use them on actual Mainnet or even the public testnets.
2. Take note of the private key and address of the first test account.

<h3>Import wallet : </h3>

Let's go ahead and import these to our MetaMask Wallet.
First, connect to the localhost network. To do this, click on the Network dropdown (top mid) of MetaMask and select localhost. Rest of the configurations are fine.
Then, ```Account -> Import Account```. Then paste your private key (for first test account) in there. You should have ```10,000 ETH``` in there. They're not too useful though so don't get excited. Let's call this hh-test0x account.

<h3>Creating New wallet : (outside Hardhat) </h3>

Let's create a new account outside of Hardhat and send it some Ether.
Go to Metamask and Account ```-> Create Account```. Give it a useful name. I'm using recly-test0x. Keep this account safe for now. We'll be using it later on. Save the private key by going to ... menu (the dots menu), then Account Details. Click on Export Private Key. Enter the password for MetaMask and save your private key somewhere. All of these are test keys and should defnitely not be used on mainnet.
Switch to ```hh-test0x``` account and send some ether to recly-test0x. (When you do this again the next time you start this tutorial from scratch, you will get a nonce error. For that, simply go to``` Accounts -> Settings -> Advanced -> Reset Account.)```

**Note**: **the output in console as well as ether, changes in your MetaMask accounts.** 
 


![image](https://user-images.githubusercontent.com/62806277/159704382-330fb927-5530-4138-80f4-83f8aea52588.png)




<h1>POST 4 </h1>


Deploying the Greeter Smart Contract
A deploy script is created for you by Hardhat automatically. Just change it to a more meaningful name.To change the name use this command:


``` mv scripts/sample-script.js scripts/deploy.js ```

Take a look at the script and then go ahead and deploy the contract. Since this is a hello world, there isn't anything we need to change.

Use vi or gedit

In my case I will use gedit

``` gedit scripts/deploy.js ```

<h3>Now to Deploy the contract use this following command:</h3>



``` npx hardhat run scripts/deploy.js --network localhost ```

![image](https://user-images.githubusercontent.com/62566404/159721212-8cd2a8a6-7a3b-44d0-8d6d-c11b33e737fb.png)


We will get an output that tells us the address (or ID) of this contract.

Greeter deployed to:``` 0x9fE46736679d2D9a65F0992F2272dE9f3c7fa6e0```

Keep track of this address. We'll need it to interact with our contract.

![image](https://user-images.githubusercontent.com/62566404/159710586-19e64530-2f2d-44a1-a749-046dc70ee816.png)

![image](https://user-images.githubusercontent.com/62566404/159710647-53d0ef32-22e6-4df0-b6b4-651259258d12.png)
 
 
 <h1>POST 5 </h1>
<h2> Accessing from React App</h2>
Use the following basic code to access the contract. We'll discuss the code in detail but for now, just put the following content in 

```src/App.js file```

**Now that the file is open,Put all the code given below into the App.js file**

Remember the Greeter address from before? Keep this in mind

![2](https://user-images.githubusercontent.com/62566404/159723491-dbe3e2df-1a72-41cc-aa22-89a0c426aae2.PNG)

```
import './App.css';
import { useState } from 'react';
import { ethers } from 'ethers'   // acts like a backend for our Web3/DApp 
import Greeter from './artifacts/contracts/Greeter.sol/Greeter.json'

// Update with the contract address logged out to the CLI when it was deployed 
// !!!!!!!! Change this ..... 
const greeterAddress = "0x5FbDB2315678afecb367f032d93F642f64180aa3"

function App() {
  // store greeting in local state of react. Has nothing to do with the smart contract at the moment
  const [greeting, setGreetingValue] = useState()

  // request access to the user's account. This works regardless of the wallet you're using. 
  async function requestAccount() {
    await window.ethereum.request({ method: 'eth_requestAccounts' });
  }

  // call the smart contract, read the current greeting value
  async function fetchGreeting() {
    if (typeof window.ethereum !== 'undefined') {
      const provider = new ethers.providers.Web3Provider(window.ethereum)
      const contract = new ethers.Contract(greeterAddress, Greeter.abi, provider)
      try {
        const data = await contract.greet()
        console.log('data: ', data)
      } catch (err) {
        console.log("Error: ", err)
      }
    }    
  }

  // call the smart contract, send an update
  async function setGreeting() {
    if (!greeting) return
    if (typeof window.ethereum !== 'undefined') {
      await requestAccount()
      const provider = new ethers.providers.Web3Provider(window.ethereum);
      const signer = provider.getSigner()
      const contract = new ethers.Contract(greeterAddress, Greeter.abi, signer)
      const transaction = await contract.setGreeting(greeting)
      await transaction.wait()
      fetchGreeting()
    }
  }

  return (
    <div className="App">
      <header className="App-header">
        <button onClick={fetchGreeting}>Fetch Greeting</button>
        <button onClick={setGreeting}>Set Greeting</button>
        <input onChange={e => setGreetingValue(e.target.value)} placeholder="Set greeting" />
      </header>
    </div>
  );
}

export default App;

```

You will see something like this 

![image](https://user-images.githubusercontent.com/62566404/159724690-c1ccabf6-f16a-4e93-ae47-69f8b774b2ca.png)









Now put this following address into the const greeterAddress 

![2](https://user-images.githubusercontent.com/62566404/159723700-2923275d-7183-434c-af49-ec79c38a00f2.PNG)

like this:


![image](https://user-images.githubusercontent.com/62566404/159725020-89923dab-f882-4eaa-8dd0-dc513d8d82ee.png)


then save the file. *Do not forget to save all the files while you are editing them :)*


Go ahead and start the npm test server on your local machine. This will let us interact with out contract through a web frontend.


``` npm start ```



![image](https://user-images.githubusercontent.com/62566404/159725368-8eea27d6-19ab-421f-b627-4a07091557f3.png)




Use the localhost address given above and copy paste that into your broswer



The app should open in your browser.


Open Developer console and then click on the Get Greeting button. Take a look at the console where hardhat will output transaction/read details for you.
Then, enter some text in the textbox and click on Set Greeting. You should get a popup in MetaMask asking you to select an account. Select the account you have balance in and connect. MetaMask will show you the gas required to run this transaction. Click ahead to run the transaction.
See the console for hardhat that looks like this:


 
![image](https://user-images.githubusercontent.com/62566404/159711664-dc541f86-3481-4b58-ac0e-ef654da00ec6.png)


```
eth_sendRawTransaction
  Contract call:       Greeter#setGreeting
  Transaction:         0xf69ac559e520e58f5e647820a3a14cbd1f18861a8bc1b71911dfbb2da8e33a78
  From:                0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
  To:                  0x5fbdb2315678afecb367f032d93f642f64180aa3
  Value:               0 ETH
  Gas used:            35330 of 35606
  Block #2:            0x098e048300fe12ae0812dd7c067bd274bd848481f57bcbbd94153f0b3b366636

  console.log:
    Changing greeting from 'Hello, Hardhat!' to 'New Greeting!'
```
 
 



 
open your your metamask in the browser to see the working,Like this:


![image](https://user-images.githubusercontent.com/62566404/159726806-30bcd91d-7030-436c-a29b-8c831a36cfaf.png)


 
Again, if you are re-doing the tutorial, reset the account in MetaMask to get rid of the stale state information in MetaMask.



<h1>POST 6 </h1>


<h2>Let's Mint a New Token </h2>



In this section, we are going to create a new Token called REC. This will be a sub currency and will showcase "reads" and "writes" to the Ethereum blockchain.

First of start by creating a new  contract by pasting the following code in contracts/Token.sol:

```
//SPDX-License-Identifier: MIT pragma solidity ^0.8.0;
import "hardhat/console.sol"; contract Token {
 	string public name = "Recluze Token";
 	string public symbol = "REC";
 	uint public totalSupply = 1000;

 	mapping(address => uint) balances;

 	constructor() {
 	balances[msg.sender] = totalSupply;
 	}

 	function transfer(address to, uint amount) external {
 	require(balances[msg.sender] >= amount, "Insufficient tokens");
 	balances[msg.sender] -= amount;
 	}

 	function balanceOf(address account) external view returns (uint) {
 	return balances[account];
 	}
}
 
```

Compile the contract as before.

```
npx hardhat compile


Make the needed changes in scripts/deploy.js so that this contract is also deployed alongside the greeter.

// in function main, add the following
const Token = await hre.ethers.getContractFactory("Token"); const token = await Token.deploy();
await token.deployed();
console.log("Token deployed to:", token.address);

```

Then let's deploy it.

```
npx hardhat run scripts/deploy.js --network localhost

```
Take note of the token address. We'll need it.

Go to MetaMask and click on Import Token in the main window. Paste the address of the token we just created. Set Decimal to 0 if needed. Now you should have the REC token added with the amount properly set.

You can transfer REC token to another account as you can ETH. Of course, you'll need ETH for gas during transaction writing. Go ahead and transfer some RECs to recly-test0x account.

![image](https://user-images.githubusercontent.com/100485149/159700776-dfb9e68d-3311-48cd-9d68-79f21d6c4c5d.png)




 
<h2> Sending and Receiving Tokens using Web Frontend </h2>
Add the following two functions to src/App.js.

```
// ...

import Token from './artifacts/contracts/Token.sol/Token.json'
// ...

const tokenAddress = "0x5FC8d32690cc91D4c39d9d3abcBD16989F875707"	// !!! Change this
// ...

// Within App()

const [userAccount, setUserAccount] = useState() const [amount, setAmount] = useState()

async function getBalance() {
 	const [account] = await window.ethereum.request({ method: 'eth_requestAccounts' })
 
ethers.providers.Web3Provider(window.ethereum);
 
 	const contract = new ethers.Contract(tokenAddress, Token.abi, provider)
 	const balance = await contract.balanceOf(account);

 
 	}

// ...

async function sendCoins() {
 	if (typeof window.ethereum !== 'undefined') {
await requestAccount()
const	provider	=	new	
ethers.providers.Web3Provider(window.ethereum);
 	const contract = new ethers.Contract(tokenAddress, Token.abi, signer);
 	const transation = await contract.transfer(userAccount, amount);
 
 	console.log(`${amount} Coins successfully sent to
${userAccount}`);
 	}

// ...
```

Also add the following in the React template in the same file:

```
   <br />
 	<button onClick={getBalance}>Get Balance</button>
 	<button onClick={sendCoins}>Send Coins</button>
 	<input onChange={e => setUserAccount(e.target.value)} placeholder="Account ID" />
 	<input onChange={e => setAmount(e.target.value)} placeholder="Amount" />
 
 ```
Start the npm server again.

``` 
npm start 
```

In the server, click on Get Balance to get the REC balance. Copy the Account ID of
recly-test0x and send 20 REC to that account. MetaMask will ask you to connect your
account if it's been a while. You can now go ahead and send the REC. Check the balance again on both accounts to ensure RECs have been transferred.


<h1>Post 7</h1>

<h2>Deploying on the Public/Global Ropsten Network</h2>
Now let's do the same with the online Ropsten Testnet because we actually want to have this app distributed! It is supposed to be a DApp after all!

<h3>Get Some Fake Ether on the Testnet</h3>
The very first thing you need to do is get some ETH in your account. For this you need to use a faucet. These are available for free and can be found by searching for "ropsten
 faucet". At the moment, the following faucets work:

●	https://faucet.ropsten.be/

●	https://faucet.metamask.io/

●	https://faucet.dimensions.network/

Request ETH on all the faucets. You'll need it for testing and it sometimes takes time to
receive it. Make sure you give it an address that you created yourself. Hardhat accounts are publicly known and people will steal your (fake) ether from the testnet and you won't be able to test out your contracts.

<h3>Get Endpoints</h3>
Next, let's create a project in Infura. This will give us an endpoint through which we can actually push our contract. Think of this as the equivalent of the node that we created locally. For the internet, you need some node to act on your behalf. We'll use infura but you can also use Alchemy.

Go to infura.io and create a new Etherium project. You need the Project ID. Also select Ropsten from the Endpoints dropdown and get the endpoint URL. Save both of these somewhere.
 
Also in the security tab, enter your public key (not the private key!) for the account
 recly-test0x account. This is because we have some test ETH in this account and we'll need that to deploy our contracts.

Stop the hardhat node and let's configure it to use the Ropsten Testnet. Edit the hardhat.config.js file and add the configs for Ropsten.
 
 

 
 

 
``` 
"https://ropsten.infura.io/v3/e5143812e60d4048a480d4fde5??????",	//
 Ropsten endpoint

 "0x261e20914b939aec2aa0529c115c8970dfa949e021bb6b0f3bef40faad??????"
 // private key with ETH
 	}
 }


 npx hardhat run scripts/deploy.js --network ropsten

```

This will use up your ETH, which you can verify through MetaMask. Go to dots menu for
 recly-test0x account and click on View on Etherscan.

You can now go ahead and import the REC token which is now on the Ropsten Testnet but is an actual DApp!

Congrats!


<h3>Deploying on Mainnet</h3>

 
Deploying on mainnet is exactly the same as with Ropsten. You can get an endpoint for mainnet from Infura. The difference is only that you will need real ETH to deploy your DApp on mainnet and it would take gas to write transactions to the block.

So, test well on the testnets and only move to the mainnet when you are sure everything is fine.

Good luck!










