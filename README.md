Catch the live running project at https://5dttj-2yaaa-aaaal-qch7a-cai.raw.icp0.io/

# TokenHarbor

DFaucet is an authenticated decentralized platform that provides users with the opportunity to claim free tokens and engage in seamless token transactions using their principal ID that serves as their digital wallet addresses within the platform. The site is designed to offer a user-friendly experience, making it easy for both beginners and experienced users to navigate and take advantage of its features.

## Features

- Users can log in to DFaucet and claim free tokens. This feature encourages user engagement and participation in the platform.
- TokenHarbor allows users to send tokens to others effortlessly. This feature promotes a decentralized and efficient way of transferring value within the platform.
- The platform boasts an intuitive and user-friendly interface, making it easy for users to navigate and access the various features offered by the platform.
- Each user is assigned a unique principal ID, serving as their digital wallet address within the platform. This ID is used for both receiving and sending tokens, adding an extra layer of security and personalization.
- Users can easily check their token balance on the platform. This transparency allows users to keep track of their holdings and monitor their activity within the platform.

## NECESSARY STEPS FOR WORKING ON THIS PROJECT

# Check your Balance

1. Find out your principal id:

```
dfx identity get-principal
```

2. Save it somewhere.

e.g. My principal id is: " "

3. Format and store it in a command line variable:

```
OWNER_PUBLIC_KEY="principal \"$( \dfx identity get-principal )\""
```

4. Check that step 3 worked by printing it out:

```
echo $OWNER_PUBLIC_KEY
```

5. Check the owner's balance:

```
dfx canister call token balanceOf "( $OWNER_PUBLIC_KEY )"
```

# Charge the Canister

1. Check canister ID:

```
dfx canister id token
```

2. Save canister ID into a command line variable:

```
CANISTER_PUBLIC_KEY="principal \"$( \dfx canister id token )\""
```

3. Check canister ID has been successfully saved:

```
echo $CANISTER_PUBLIC_KEY
```

4. Transfer half a billion tokens to the canister Principal ID:

```
dfx canister call token transfer "($CANISTER_PUBLIC_KEY, 500_000_000)"
```

# Deploy the Project to the Live IC Network

1. Create and deploy canisters:

```
dfx deploy --network ic
```

2. Check the live canister ID:

```
dfx canister --network ic id token
```

3. Save the live canister ID to a command line variable:

```
LIVE_CANISTER_KEY="principal \"$( \dfx canister --network ic id token )\""
```

4. Check that it worked:

```
echo $LIVE_CANISTER_KEY
```

5. Transfer some tokens to the live canister:

```
dfx canister --network ic call token transfer "($LIVE_CANISTER_KEY, 50_000_000)"
```

6. Get live canister front-end id:

```
dfx canister --network ic id token_assets
```

7. Copy the id from step 6 and add .raw.ic0.app to the end to form a URL.
   e.g. blah-blah-blah.raw.ic0.app
