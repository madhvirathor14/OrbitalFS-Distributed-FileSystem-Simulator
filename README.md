# OrbitalFS-Distributed-FileSystem-Simulator
A lightweight distributed file-system simulator that splits files into chunks, distributes them across simulated satellite nodes, and reconstructs them with integrity checks. 
OrbitalFS is a lightweight distributed file-system simulation designed for CosmoHack (PS1 – COSMEON FS-Lite).
It demonstrates how files can be split into chunks, distributed across satellite-like nodes, and reconstructed even under node failures — similar to distributed storage used in orbital data networks.

🚀 Project Overview

Real satellite systems require storing and sharing data across multiple orbital nodes.
OrbitalFS simulates this by:

Splitting files into multiple chunks

Distributing chunks across multiple simulated “satellite nodes”

Tracking each chunk via metadata

Reconstructing the original file from chunks

Handling node failures

Verifying file integrity using hashing

This project provides a clear understanding of distributed storage fundamentals.

🎯 Features
✔ File Chunking

Divides any file into equal-sized chunks.

✔ Chunk Distribution to Nodes

Assigns chunks to multiple simulated satellite nodes using round-robin strategy.

✔ Metadata Tracking

Stores:

Chunk name

Node where chunk is stored

Sequence index

Integrity hash

✔ File Reconstruction

Fetches chunks from nodes and merges them back to recreate the original file.

✔ Node Failure Simulation

Simulate missing/unavailable nodes to observe system behavior.

✔ Integrity Check

Uses SHA-256 hashing to ensure no chunk is corrupted or altered.

✔ Fully Modular Code

Each component is separated into different modules:

chunker.py

distributor.py

metadata_manager.py

reconstruct.py

node_simulator.py

integrity_checker.py

🛰️ System Architecture
           +------------------+
           |   Input File     |
           +--------+---------+
                    |
                    v
      +----------------------------+
      |        Chunker.py          |
      | (Splits file into chunks)  |
      +-------------+--------------+
                    |
                    v
      +----------------------------+
      |     Distributor.py         |
      | (Distributes chunks to     |
      |  satellite nodes)          |
      +-----+---------+------------+
            |         |
            v         v
     [Node1] [Node2] [Node3] ... (Simulated satellite nodes)

                    |
                    v
        +--------------------------+
        |   Metadata Manager       |
        | (Stores chunk mapping)   |
        +-------------+------------+

                    |
                    v
        +--------------------------+
        |     Reconstruct.py       |
        | (Fetch + merge chunks)   |
        +-------------+------------+

                    |
                    v
        +--------------------------+
        |  Final Output File       |
        +--------------------------+

📁 Folder Structure
OrbitalFS/
│
├── src/
│   ├── chunker.py
│   ├── distributor.py
│   ├── metadata_manager.py
│   ├── reconstruct.py
│   ├── node_simulator.py
│   └── integrity_checker.py
│
├── nodes/
│   ├── node1/
│   ├── node2/
│   └── node3/
│
├── samples/
│   └── testfile.txt
│
├── README.md
└── requirements.txt

⚙️ Tech Stack

Python 3

Hashlib (SHA-256 Integrity Check)

JSON (Metadata Storage)

Local folders as simulated nodes

Optional: React.js / CLI interface (future upgrades)

🧪 How To Run
1️⃣ Install dependencies
pip install -r requirements.txt

2️⃣ Chunk a file
python src/chunker.py samples/testfile.txt

3️⃣ Distribute chunks to nodes
python src/distributor.py

4️⃣ Reconstruct the file
python src/reconstruct.py

5️⃣ Simulate node failure

Delete any node folder (e.g., nodes/node2)
Then run reconstruction again to see behavior.

📊 Example Output
[+] Splitting file into chunks...
[+] 3 chunks created.
[+] Distributing chunks to nodes...
[+] Chunk_1 → node1
[+] Chunk_2 → node2
[+] Chunk_3 → node3
[+] Metadata stored successfully.
[+] Integrity check passed.

[+] Reconstructing file...
[+] All chunks fetched successfully.
[+] File reconstructed: output/reconstructed_file.txt

❗ Node Failure Simulation Example
[-] Warning: node2 unavailable!
[-] Missing chunk: chunk_2
[x] File reconstruction failed due to missing data.

📌 Use Cases

Ideal learning model for distributed systems

Demonstrates satellite-like orbital data flow

Good foundation for advanced replication, sharding, redundancy


🏁 Conclusion

OrbitalFS is a simple yet powerful simulation of how distributed file storage works in multi-node orbital environments.
It fulfills all PS1 requirements — chunking, distribution, metadata, reconstruction, node failure handling, and integrity checks.

This project is fully extensible and provides a solid base for future development in real satellite-based distributed storage systems.

👨‍💻 Author

Team Name: Code Conqueror
Team Leader: Madhvi Rathore
