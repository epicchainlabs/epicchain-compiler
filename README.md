## EpicChain Compiler Suite

[![Open in Gitpod](https://gitpod.io/button/open-in-gitpod.svg)](https://gitpod.io/#/https://github.com/epicchain/epicchain-compiler/)
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/EpicChain/epicchain-compiler)

Welcome to the EpicChain Compiler Suite! This is a comprehensive, open-source initiative designed to provide seamless access and interaction with the EpicChain ecosystem. Our suite offers user-friendly interfaces for compiling code in various languages directly within the EpicChain environment.

### Key Features

- **Multi-Language Compilation:** Our suite supports compiling code written in C#, Python, Go, and Java. This ensures broad compatibility with different programming needs and environments.
- **User-Friendly Interfaces:** Simple and interactive interfaces are designed for ease of use, making code compilation and deployment straightforward.
- **Online Compilation:** Directly compile your code online without the need for local installations or configurations.

**Official Documentation on [ReadTheDocs](https://epicchain-compiler.readthedocs.io)**

[![Documentation Status](https://readthedocs.org/projects/epicchain-compiler/badge/?version=latest)](https://epicchain-compiler.readthedocs.io/en/latest/?badge=latest)

#### Building Documentation Locally

To build the documentation locally, run `./make-docs.sh`, and navigate to `./docs/build/html/index.html` for the local version of the documentation.

### Access Points

- **Web Interface:** The current front-end interface can be accessed at [https://epicchain-compiler.io](https://epicchain-compiler.io), automatically generated from the source code in this repository.
- **Compilers RPC API:** Available at [https://compilers-epicchain.io/](https://compilers-epicchain.io)
- **Additional Services:**
  - [https://ecoservices-epicchain.io](https://ecoservices-epicchain.io)
  - Includes a shared private network with four consensus nodes.
  - C# RPC node with watch-only feature.

### Current Capabilities

- **Code Compilation:** Compile input code in C# using reliable and secure backend compilers.
- **File Generation:** Produce NEF-compatible files, including AVM, ABI, and MANIFEST codes.
- **Code Deployment:** Deploy and invoke code on private net, shared private net, testnet (unsafe), and mainnet (unsafe).
- **Activity History:** Save and review your activity history for testing smart contracts.
- **Wallet Testing:** Test with various wallets, synced and capable of providing historical data.
- **Blockchain Interaction:** Perform up-to-date blockchain invocations and RPC calls.
- **Real-Time Information:** Utilize websockets to receive useful information.
- **Network Compatibility:** Operate on both TestNet and MainNet environments.

### Roadmap

- **Future Enhancements:** Transition towards client-based compiling to improve security, robustness, and scalability.
- **Community Involvement:** We welcome ideas and collaborations to enhance our suite. Our goal is to educate and bring technology closer to users, with a focus on Smart Cities, Smart Governance, and Smart Blockchain Technologies.

### Dependencies and Setup

**Docker Recommendations:**

Docker is essential for sandboxing compilers in separate environments for different languages. Docker Compose is integrated with Docker Desktop.

* Ubuntu-based distributions [guidelines](https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository):

```bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

If necessary, add your user to the Docker group: `sudo usermod -a -G docker $USER`

**Building Everything:**

To create your own EpicChain Compiler Suite, suitable for both private and public blockchain projects, use:

```bash
./build_everything.sh
```

This command will execute a Docker Compose setup with EpicChain Private Net (Eco) and optionally, EpicChain Scan. It will also set up all available compilers and open the front-end and back-end interfaces.

### Developer Guidelines

#### A1) Building Compilers

To build compilers and start the server, use:

```bash
./docker-sock-express-compilers/docker-compilers/buildCompilers.sh
```

* Modify `./docker-sock-express-compilers/docker-compilers/.env` to build different compilers (e.g., `BUILD_ALL_CSHARP=0`).
* Build lists with different versions of a compiler using:

```bash
docker-sock-express-compilers/docker-compilers/compilers/docker-compiler-csharp/docker_build_list_of_compilers.sh
```

#### A2) Eco Network Functionalities

Docker Compose is utilized for creating our micro-services. To start all necessary backend functionalities and EpicChain nodes, use:

* Start up the container and monitor messages and warnings with:

```bash
runEco_network.sh
```

or:

```bash
cd ./docker-compose-eco-network
docker compose up
```

* For detached mode:

```bash
docker compose up -d
```

* To stop and restart:

```bash
docker compose stop
docker compose start
```

### Useful Commands

* **Open C# Nodes:**

```bash
docker exec -it eco-neo-csharp-node1-running bash
screen -dr
/opt/run.sh
/opt/start_node.sh
```

### Contributing

We welcome contributions and feedback! Here's how you can get involved:

1. Check open [issues](https://github.com/EpicChain/epicchain-compiler/issues) and [pull requests](https://github.com/EpicChain/epicchain-compiler/pulls) for ongoing discussions.
2. Open a new issue to discuss features or enhancements.
3. Write tests and ensure the test suite passes both locally and on CI.
4. Open a pull request, referencing relevant issues.
5. After feedback, squash commits and add a detailed commit message.
6. Run `make push-tag` after merging your pull request.

*Our team consists of researchers and professors, so our time is limited. If you can assist, please do! We also accept donations to support server improvements and further development. NEO wallet for donations: __AJX1jGfj3qPBbpAKjY527nPbnrnvSx9nCg__*

**LICENSE MIT**

This project is part of the EpicChain initiative and is freely available at [EpicChain.io](https://epicchain-compiler.io). The website is periodically rebooted to manage resource usage.

*EpicChain Compiler Suite Team* [@epicdev](https://github.com/epicdev) and [@epicresearch](https://github.com/epicresearch)

Copyleft 2024
