Initialize the repository:

```bash
cd ${HOME}/glitch-hackathon-test
forge init

git remote add origin git@github.com:ava-labs/glitch-hackathon-test.git
git push -u origin main
```

Install the dependencies:

```bash
cd ${HOME}/glitch-hackathon-test

# forge install NomicFoundation/hardhat
# forge install https://github.com/NomicFoundation/hardhat

# forge install openzeppelin/openzeppelin-contracts
forge install https://github.com/OpenZeppelin/openzeppelin-contracts

# ref. https://github.com/opengsn/gsn/releases
forge install opengsn/gsn@v3.0.0-beta.7
#
# once "v3*" gets merged to its main branch
# forge install https://github.com/opengsn/gsn
```

Copy the trusted forwarder contract from [OpenGSN](https://github.com/opengsn/gsn):

```bash
cd ${HOME}/glitch-hackathon-test
# vi ./lib/gsn/packages/contracts/src/forwarder/Forwarder.sol
cp ./lib/gsn/packages/contracts/src/forwarder/Forwarder.sol src/Forwarder.sol
cp ./lib/gsn/packages/contracts/src/forwarder/IForwarder.sol src/IForwarder.sol
```

Write the dependency remapping file:

```bash
cd ${HOME}/glitch-hackathon-test
cat << EOF > remappings.txt
@opengsn/=lib/gsn/packages/
@openzeppelin/=lib/openzeppelin-contracts/
forge-std/=lib/forge-std/src/
hardhat/=lib/forge-std/src/
EOF
```

To update dependencies:

```bash
cd ${HOME}/glitch-hackathon-test
git submodule update --init --recursive

cd ${HOME}/glitch-hackathon-test
forge update
```

```bash
cd ${HOME}/glitch-hackathon-test
# vi ./lib/gsn/packages/contracts/src/forwarder/Forwarder.sol
cp ./lib/gsn/packages/contracts/src/forwarder/Forwarder.sol src/Forwarder.sol
cp ./lib/gsn/packages/contracts/src/forwarder/IForwarder.sol src/IForwarder.sol
```
