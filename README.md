content-hash<br>
npm packageCircleCIlicenceGitter chatBeerpay

This is a simple package made for encoding and decoding content hashes. This package will be useful for every Ethereum developer wanting to interact with compliant domain resolvers.

Here you can find a live demo of this package.

link to npm
link to Github
🔠 Supported Codec
swarm-ns
ipfs-ns
ipns-ns
Every other codec supported by multicodec will be encoded by default in utf-8.
You can see the full list of codec supported here

📥 Install
via npm :
 $> npm install content-hash
via Github : Download or clone this repo, then install the dependencies.
 $> git clone https://github.com/pldespaigne/content-hash.git
 $> cd content-hash
 $> npm install
For browser only usage, installation is not required.

🛠 Usage
Import the module in order to use it :

NodeJS :
 const contentHash = require('content-hash')
Browser :
 <!--From CDN-->
 <script type="text/javascript" src="https://unpkg.com/content-hash/dist/index.js"></script>

 <!--From local module-->
 <script type="text/javascript" src="path/to/dist/index.js"></script>
To rebuild the browser version of the package run npm run build into the root folder. Don't forget to also run npm run lint and npm test before building !

📕 API
All hex string inputs can be prefixed with 0x, but it's not mandatory.

⚠️ All outputs are NOT prefixed with 0x

contentHash.decode( contentHash ) -> string
This function takes a content hash as a hex string and returns the decoded content as a string.

const encoded = 'e3010170122029f2d17be6139079dc48696d1f582a8530eb9805b561eda517e22a892c7e3f1f'

const content = contentHash.decode(encoded)
// 'QmRAQB6YaCyidP37UdDnjFY5vQuiBrcqdyoW1CuDgwxkD4'
contentHash.fromIpfs( ipfsHash ) -> string
This function takes an IPFS address as a base58 encoded string and returns the encoded content hash as a hex string.

this function just call contentHash.encode() under the hood

const ipfsHash = 'QmRAQB6YaCyidP37UdDnjFY5vQuiBrcqdyoW1CuDgwxkD4'

const contentH = contentHash.fromIpfs(ipfsHash)
// 'e3010170122029f2d17be6139079dc48696d1f582a8530eb9805b561eda517e22a892c7e3f1f'
contentHash.fromSwarm( swarmHash ) -> string
This function takes a Swarm address as a hex string and returns the encoded content hash as a hex string.

this function just call contentHash.encode() under the hood

const swarmHash = 'd1de9994b4d039f6548d191eb26786769f580809256b4685ef316805265ea162'

const contentH = contentHash.fromSwarm(swarmHash)
// 'e40101701b20d1de9994b4d039f6548d191eb26786769f580809256b4685ef316805265ea162'
contentHash.encode( codec, value) -> string
This function takes a supported codec as a string and a value as a string and returns coresponding content hash as a hex string.

const onion = 'zqktlwi4fecvo6ri'
contentHash.encode('onion', onion);
// 'bc037a716b746c776934666563766f367269'
contentHash.getCodec( contentHash ) -> string
This function takes a content hash as a hex string and returns the codec as a hex string.

const encoded = 'e40101701b20d1de9994b4d039f6548d191eb26786769f580809256b4685ef316805265ea162'

const codec = contentHash.getCodec(encoded) // 'swarm-ns'
codec === 'ipfs-ns' // false
contentHash.helpers
This object contain the following helpers functions :

cidV0ToV1Base32( ipfsHash ) -> string
This function takes an ipfsHash and convert it to a CID v1 encoded in base32.
 const ipfs = 'QmYwAPJzv5CZsnA625s3Xf2nemtYgPpHdWEz79ojWnPbdG'

 const cidV1 = contentHash.helpers.cidV0ToV1Base32(ipfs)
 // 'bafybeibj6lixxzqtsb45ysdjnupvqkufgdvzqbnvmhw2kf7cfkesy7r7d4'
👨‍💻 Maintainer
pldespaigne : github, twitter
🙌 Contributing
For any questions, discussions, bug report, or whatever I will be happy to answer through the issues or on my twitter 😁. PR (with tests) are also welcome !

📝 License
This project is licensed under the ISC License, you can find it here.

Note that the dependencies may have a different License
