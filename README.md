# Basic_BlockChain
This is a basic blockchain made in google colab 

# Execute

To run this project, simply open the BlockChain.ipyn file and click on the run button in Colab. Once there, execute all cells in order as they appear, and after executing the last cell, the entire program will start running through the console, where you will also enter the data intended to be included in the block and the chain. In this case, the data to be entered is just any phrase, without a character limit.
Then, the program itself will show the results, such as the hash of the previous block, the Merkle tree root, the nonce, among others.
To finish it, simply stop the execution of the last cell or directly follow the program's instructions to stop the execution.

# General Operation of the Code

1. **Creation of the Blockchain:**
   - The user decides whether to start creating the chain.
   - An initial or genesis block is created if the chain is empty, or a new block is created with the data provided by the user.
   - The validity of the transaction is verified before adding the block to the chain.
   - If the transaction is valid, the block is mined and added to the chain.

2. **Block Mining:**
   - The `mine` method of the `Blockchain` class is responsible for mining a block.
   - The Merkle tree root is set for the block.
   - The block's hash is computed until it meets the specified difficulty.

3. **Transaction Verification:**
   - The `verify_transaction` method of the `Block` class verifies if a transaction is valid.
   - It checks that the length of the transaction data is greater than zero.
   - It verifies if the transaction already exists in the current block.

4. **Printing the Blockchain:**
   - The `print_chain` method of the `Blockchain` class prints the entire blockchain.
   - Information about each block is printed, including the nonce, the Merkle tree root, the hash of the previous block, and the block's data.

5. **User Interaction:**
   - The user can decide whether to continue adding blocks to the chain.
   - The user is asked if they want to continue adding blocks after each block is added to the chain.

6. **Ending the Program:**
   - The user can stop the execution of the program at any time.
   - The user is asked if they want to create a new chain after the current chain is completed.

In summary, the code implements a basic blockchain system that allows the user to create a chain of blocks, add new blocks with transactions, and verify the validity of transactions. It also displays detailed information about each block and allows the user to interact with the program through the console.


# Explanation of Methods and Classes Used in the Code

## Class `MerkleTree`

### Constructor (`__init__`)
- **Purpose:** Initializes the class with a list of transactions and calls the `build_tree` method to construct the Merkle tree.
- **Parameters:** `transactions` (list of transactions, information to be put into the tree).
- **Actions:** Calls `build_tree`.

### Method `build_tree`
- **Purpose:** Constructs the Merkle tree from the list of transactions.
- **Actions:**
  - Checks if the number of transactions is even and adjusts the list if necessary, if it is odd it adds the last element of the list to make the tree.
  - Fills the tree with the transaction hashes.
- **Returns:** The Merkle tree.

### Method `get_root`
- **Purpose:** Returns the root of the Merkle tree.
- **Returns:** The root of the tree.

## Class `Block`

### Constructor (`__init__`)
- **Purpose:** Initializes a block with the hash of the previous block, the block's data, the nonce, and the Merkle tree root.
- **Parameters:** `previous_block` (hash of the previous block), `data` (block's data).
- **Actions:** Sets the block's attributes.

### Method `hashCreator`
- **Purpose:** Creates the block's hash using the Merkle tree root, the block's data, the hash of the previous block, and the nonce; uses the hashlib library.
- **Actions:** Computes and returns the block's hash.

### Method `set_merkle_root`
- **Purpose:** Sets the Merkle tree root for the block.
- **Parameters:** `merkle_root` (Merkle tree root).

### Method `print_info`
- **Purpose:** Prints the block's information.
- **Actions:** Prints the nonce, the Merkle tree root, the hash of the previous block, and the block's data.

### Method `verify_transaction`
- **Purpose:** Verifies if the block's transaction is valid.
- **Parameters:** `block_chain` (blockchain).
- **Actions:**
  - Checks if the length of the transaction data is greater than zero.
  - Verifies if the transaction already exists in the current block.
- **Returns:** True if the transaction is valid, False otherwise.

## Class `Blockchain`

### Constructor (`__init__`)
- **Purpose:** Initializes the blockchain as an empty list.

### Method `add`
- **Purpose:** Adds a block to the chain.
- **Parameters:** `block` (block to add).

### Method `mine`
- **Purpose:** Mines a block.
- **Parameters:** `block` (block to mine).
- **Actions:**
  - Sets the Merkle tree root.
  - Computes the hash until the specified difficulty is met.

### Method `calculate_merkle_root`
- **Purpose:** Calculates the Merkle tree root of the blockchain.
- **Actions:** Creates a list of transactions from the chain and calculates the tree root.

### Method `print_chain`
- **Purpose:** Prints the entire blockchain.

## Additional Functions and Variables
- **`createBlock` and `createChain`:** Functions that interact with the user to create new blocks and add them to the chain.
- **`pregunta`:** Function that asks the user if they want to continue adding blocks to the chain.
- **`User` and `contador`:** Variables to control user interaction and the number of mined blocks.
