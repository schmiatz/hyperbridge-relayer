# What does this Repo?
This Repo contains an ansible Playbook, that will install Docker on your Ubuntu 22.04 Server, that will create a Hyperbridge-Relayer Container on your Machine.    

# How to use this Playbook?

## Requirements:
To use this Playbook you need:
- ssh access to a Machine with a user that has root permissions
- ansible installed on the Machine you want to execute the Playbook from
- declare some Varibales

## Variables to declare
### In the file 'group_vars/all.yml' you need to change this variables:
- system_username
- etherscan_api_key
- eth_rpc
- arbitrum_rpc
- optimism_rpc
- base_rpc
- bsc_rpc
- signer

### Examples and explanation
#### system_username
Thats the username of your Ubuntu/Debian User.
If you login into your System for example with the command 'ssh hyperbridge@<IP-ADDRESS>' your system_username is 'hyperbridge'.   
```
system_username: hyperbridge
```

#### etherscan_api_key
You need to specify your etherscan API here.    
[How to create this key](https://docs.etherscan.io/getting-started/viewing-api-usage-statistics)

#### eth_rpc and all the other _rpc variables
Here you need to define the RPC http(s) addresses of the Sepolia RPCs you want to connect to the relayer.    
You dont have to connect all the chains, two are enough to run the relayer.   
Just leave the rpc variables that you dont want to use commented out.   

#### signer
The Privatekey that will deliver the messages. You will need to have the native Token for the Chains on that key.   

### In the file 'inventory.yml' you need to change this variables:
- ansible_host

### Examples and explanation
#### ansible_host
Thats the IP-Address of your Target Machine.
Your Machine needs to be accessable using ssh with that IP.
```
ansible_host: 192.168.1.10
```

# Run the Playbook
## Execute Ansible
cd into this Repo and run the Playbook with 'ansible-playbook playbook.yml'

## Check your Machine after the run
Have a look in the docker logs of your newly created Container.   