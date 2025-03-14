# Distributed Network File System (NFS) Implementation
## Introduction

This project involves developing a simple distributed file system from scratch, focusing on network communication and file management. It includes key components such as clients, a naming server, and storage servers, enabling file operations like reading, writing, and streaming.

## Components and Functionalities

### Naming Server (NM)
The Naming Server acts as a central hub, managing the directory structure and maintaining essential information about file locations. It provides clients with the IP address and port of the relevant Storage Server where a requested file or folder resides.

#### Key Features:
- **Initialization:** Dynamically registers Storage Servers and clients, ensuring no hardcoded IP addresses.
- **Client Task Feedback:** Provides timely feedback to clients upon task completion.
- **Efficient Search:** Utilizes data structures like Hashmaps and Tries for fast file location searches.
- **LRU Caching:** Implements caching for recent searches to enhance response times.

### Storage Servers (SS)
Storage Servers are responsible for the physical storage and retrieval of files and folders. They manage data persistence and distribution across the network.

#### Key Features:
- **Initialization:** Registers with the Naming Server, providing IP address, ports, and accessible paths.
- **File Operations:** Supports creating, deleting, copying files/directories, and streaming audio files.
- **Client Interactions:** Handles client requests for file operations, ensuring data consistency.

### Clients
Clients represent the systems or users requesting access to files within the network file system. They initiate various file-related operations.

#### Key Features:
- **Path Finding:** Communicates with the Naming Server to locate files across Storage Servers.
- **Functionalities:** Supports reading, writing, retrieving file information, streaming audio, creating/deleting files/folders, and copying files/directories between Storage Servers.
- **Listing Paths:** Retrieves all accessible paths across registered Storage Servers.

## System Features

- **Asynchronous and Synchronous Writing:** Supports both asynchronous writes for large data inputs and synchronous priority writes when necessary.
- **Multiple Clients:** Ensures concurrent client access to the Naming Server with initial acknowledgments for received requests.
- **Error Handling:** Defines custom error codes for distinct scenarios, enhancing communication between the NFS and clients.
- **Data Replication:** Implements a replication strategy for fault tolerance, duplicating every file and folder in two other Storage Servers.
- **Failure Detection:** The Naming Server detects Storage Server failures, ensuring prompt responses to disruptions.

## Implementation Details

- **Programming Language:** C
- **Networking Protocol:** TCP Sockets
- **Concurrency Management:** Multithreading for handling multiple clients concurrently
- **Data Structures:** Hashmaps and Tries for efficient search
- **Caching:** LRU caching for recent searches
- **Tools:** Wireshark for debugging, Netcat for testing

## Setup Instructions

### Prerequisites

- **Language:** C
- **Environment:** Linux or similar Unix-based systems
- **Tools:** GCC compiler, Makefile for compilation

### Steps to Run

1. **Clone the Repository:**

2. **Navigate to the Project Directory:**
cd your-repo-name
3. **Compile the Naming Server:**
- Navigate to the `naming server` folder:
- cd naming_server
- Compile all C files in the folder:
- gcc *.c -o naming_server

4. **Compile the Storage Server:**
- Navigate to the `Storage server` folder:
- cd ../storage_serve
- Compile all C files in the folder:
- gcc *.c -o storage_server
5. **Compile the Client:**
- Navigate to the `client` folder:
- cd ../client
- Compile all C files in the folder:
- gcc *.c -o client





### Example Usage

- **Client Operations:**
- **Read File:** Send a read request with the file path to the NM.
- **Write File:** Send a write request with the file path and content to the NM.
- **Create File/Folder:** Send a create request with the path and name to the NM.

### Notes

- Ensure that the Naming Server is running before starting Storage Servers and clients.
- Use the IP address and port provided by the Naming Server to communicate with Storage Servers.
