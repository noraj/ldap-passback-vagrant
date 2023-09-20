# ldap-passback-vagrant

Quickly deploy an LDAP server with support for plaintext authentication usable for LDAP PassBack attacks.

## Deploy & run

1. Clone the repository
2. `vagrant up`
3. Choose your adapter (bridged mode)
4. `vagrant ssh` and run the following command:

```bash
sudo tshark -i any -f "port 389" -Y "ldap.protocolOp == 0 && ldap.simple" -e ldap.name -e ldap.simple -Tjson 2> /dev/null
```

## Credits

Based on [pedrojosenavasperez/ldap-passback-docker](https://github.com/pedrojosenavasperez/ldap-passback-docker) work for docker.