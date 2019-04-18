# Local Corda Network Services

Set up using instructions at: http://docs.netman.r3.com/quick-start.html

## Doorman
  - p2pAddress: 12000
  - ezmListener: 12001
  - ssh:
    - port: 12002
    - user: testuser
    - password: example-password

Start with:
```
$ cd doorman
$ java -jar doorman-0.4.jar --config-file doorman.conf --ignore-migration
```

## Notary:
  - Name: "O=NotaryA,L=London,C=GB"
  - Address: localhost:13000
  - ssh:
    - port:13002
  - rpc:
    - address: 13003
    - admin: 13004
    - rpcuser: testuser
    - rpcpassword: example-password

Initial registration:
```
$ cd notary
$ java -jar corda-4.0.jar --initial-registration --network-root-truststore-password example-password --network-root-truststore certificates/networkRootTrustStore.jks
```
Start the notary:
```
$ cd notary
$ java -jar corda-4.0.jar
```

## Network map:
  - Address: localhost:14000
  - ezmListener: 14001
  - ssh:
    - port: 14002
    - user: testuser
    - password: example-password

Initial registrations:

```
$ cd network_map
$ java -jar doorman-0.4.jar --config-file network-map.conf --set-network-parameters network-parameters.conf --network-truststore certificates/certificateStore.jks --truststore-password example-password --root-alias cordarootca --ignore-migration
```

Start the Network Map:
```
$ cd network_map
$ java -jar doorman-0.4.jar --config-file network-map.conf
```
