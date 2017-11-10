# OPENSTACK CLI

## Install OpenStack CLI

1) Downoload and install miniconda following the instructions on their website

2) Create conda environment
```sh
conda create --name os-swift
```

3) Source environment
```sh
source activate os-swift
```

4) Install Keystone, Swift and other needed packages
```sh
pip install python-keystoneclient
pip install python-swiftclient
```

5) Export environment variables containing Keystone auth configs, or request a shell script containing the below from your OpenStack provider:  
```sh
OS_AUTH_URL
OS_AUTH_TYPE
OS_PROJECT_ID
OS_PROJECT_NAME
OS_USER_DOMAIN
OS_TENANT_ID
OS_TENANT_NAME
OS_USERNAME
OS_PASSWORD
OS_REGION_NAME
OS_INTERFACE
OS_IDENTITY_API_VERSION
```

## Swift Object Store

### Commonly used CLI commands

```sh
# show statistics for this provision of swift
swift stat

# Get STORAGE_URL and OS_AUTH_TOKEN to use with curl uploads
swift auth

# Upload a "helloworld.txt" file to container called "test"
# container "test" will be created if it does not already exist
swift upload test helloworld.txt

# list all your containers in swift 
swift list

# list all the files in the container called "test"
swift list test

```

### Upload files with curl utility
This is useful because you can upload files from any computer to Swift, even if the computer does not have the Swift CLI installed.
```sh
curl -v \
    -H 'X-Auth-Token: <<OS_AUTH_TOKEN>>' \
    https://<<STORAGE_URL>>/test/hello-2.txt \
    -T hello-2.txt
```
