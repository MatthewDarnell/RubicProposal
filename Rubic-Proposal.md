Rubic-Proposal.md

# Proposal: Funding for Delivered Rubic Project

**Proposal to fund compensate Matthew for time and effort developing the Qubic Wallet, Rubic, in Rust.**

One of the critical components to a healthy coin ecosytem is a secure native desktop wallet that can be used offline. Thus far, no such wallet has been created with the average user in mind.

**Rubic** is a Qubic wallet and lite-node written from scratch in Rust. It attempts to deliver security as well as ease of use while compromising on neither. It has already been written and is available open-source for use, inspection, and development.


Feel free to view the code and download the auto-built release: [Rubic Wallet](https://github.com/matthewdarnell/rubic)

The [first git commit](https://github.com/MatthewDarnell/rubic/commit/345e68c7f730cfde8a1fbb68bb1842029c423403) for Rubic was Aug 8, 2023. Since then, there have been 200 commits.
This project has been a delight but also has taken 700+ hours.

Assets are currently being added.

---

## 🗳 Voting Options

- **Option 0:** No, do not support Rubic Wallet
- **Option 1:** Yes, approve compensating **Matthew** for development with at least **30,000,000,000 (30bn) Qus** to wallet:  
  `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`. *No Additional Development Work Wanted.*
- **Option 2:** Yes, approve compensating **Matthew** for development with at least **40,000,000,000 (40bn) Qus** to wallet:  
  `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`  
- **Option 3:** Yes, approve compensating **Matthew** for development with at least **50,000,000,000 (50bn) Qus** to wallet:  
  `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`. *Please Continue Working On Rubic.* 
- **Option 4:** Yes, approve compensating **Matthew** for development with at least **60,000,000,000 (60bn) Qus** to wallet:  
  `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`  
- **Option 5:** Yes, approve compensating **Matthew** for development with at least **70,000,000,000 (70bn) Qus** to wallet:  
  `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`  
- **Option 6:** Yes, approve compensating **Matthew** for development with **80,000,000,000 (80bn) Qus** to wallet:  
  `RUBICDEVRDOILARXMHZCUOGLEEKBKUBOEIKCIHDJVAPAWSTDASIZMRGFIVBL`. *Buy Rubic outright, Turn Over To Core Team On Payment.*

---

## 📝Vote Tallying

The final price will be the *maximum* option which received 50%+ of the vote.

For example:

| Option | Votes |
|--------|-------|
| 0      | 100   |
| 1      | 100   |
| 2      | 100   |
| 3      | 100   |
| 4      | 100   |
| 5      | 101   |

Over 50% of the votes were for Option 3 and above, so the final price would be Option 3.

---

## 	🖥 Why Rubic

Every coin needs a straightforward way to securely store keys and generate transactions. The most popular wallets currently are web and mobile based, and most applications rely on a centralized RPC provider to query balance, transaction status, etc.

Rubic runs on the Desktop in memory-safe Rust and there are very few external dependencies. It exposes a web API which can be used to build 3rd party applications.

It also maintains a peer set of real Qubic nodes, making it not only a desktop wallet, but a lite-node which communicates in real time with its Qubic peers.


---

## 🔏 Features

- Stores Seeds, Transactions, and more in a SQLite Database on the User's computer
- Generates Qu Transfer Transactions
- Tracks Identity Balances
- Realtime Communication with Qubic Nodes
- Independent Tick and Transaction Validation
- Totally Decentralized
---

## ⚙ Technical Details

1. Storage
- Seeds, Peer IPs, etc. stored in SQlite3 Database
- Always know where your info is stored, a single SQL file.

2. Cryptography
- *Functions*: Rust crate `sodiumoxide` (binding to `libsodium`) is used
- *Wallet Password*: Hashed and Salted With [Argon2](https://docs.rs/sodiumoxide/latest/sodiumoxide/crypto/pwhash/argon2id13/index.html)
- *Seed Management*: Authenticated and Encrypted with [xsalsa20poly1305](https://nacl.cr.yp.to/secretbox.html) using Wallet [Password Key Derivation](https://docs.rs/sodiumoxide/latest/sodiumoxide/crypto/pwhash/index.html)
- *Identities*: Native Rust FourQ elliptic curve and KangarooTwelve Hash allows for fast Qubic Identity Generation without external C dependencies

4. Lite-Node
- Rubic is decentralized and does not rely on any central RPC service to run.
- Maintains a PeerSet with TCP connections to its Peer Qubic Nodes
- Dynamic Peer Discovery
- Realtime Communication from Peers Queries:
  - Live Current Tick Data
  - Identity Balance (Requires at least 2 [matching Peer Responses](https://github.com/MatthewDarnell/rubic/blob/main/store/src/sqlite/identity.rs#L225))
  - Broadcasting Generated Transactions
  - Current Epoch Computors with [Verification](https://github.com/MatthewDarnell/rubic/blob/main/consensus/src/computor.rs#L40) vs Arbitrator
  - Tick with [Verification](https://github.com/MatthewDarnell/rubic/blob/main/consensus/src/quorum_votes.rs#L20) vs Computors
  - TickData with [Verification](https://github.com/MatthewDarnell/rubic/blob/main/consensus/src/tick_data.rs#L140) vs Computors and Corresponding Tick

---

## 🖼 Screenshots

**Included UI:**

<img style="max-width: 30%; max-height: 5%;" src="/images/balances.png"/>\
<img style="max-width: 30%; max-height: 5%;" src="/images/peers.png" />\
<img style="max-width: 30%; max-height: 5%;" src="/images/additional_features.png" />

**3rd Party UI Currently Under Development:**

<img style="max-width: 30%; max-height: 5%;" src="/images/tx.png" />\
<img style="max-width: 30%; max-height: 5%;" src="/images/peer.png" />\
<img style="max-width: 20%; max-height: 3%;" src="/images/pw.png" />

---

## 🕞 Possible Next Features

- Asset support
- Qx Interface
- Voting Support
- Alignment of http API with the current RPC interface so most current Qubic apps can "plug and play" with it and become truly decentralized apps.

---

## 🔥 Conclusion

This proposal might be unusual because the product is being delivered up front. It was developed out of support for the Qubic project and for the community.

Development has taken many hours of research, planning, and coding. My goal is for it to become a community project, on top of which many decentralized apps can be built.

----------

