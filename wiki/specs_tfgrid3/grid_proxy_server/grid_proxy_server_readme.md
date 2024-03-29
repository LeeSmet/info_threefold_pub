# Grid proxy server

Interact with TFgrid-DB using rest APIs

Github repo: [grid_proxy_server](https://github.com/threefoldtech/grid_proxy_server.git)

## Prerequisites

1. A msgbusd instance must be running on the node. This client uses RMB (message bus) to send messages to nodes, and get the responses.
2. A valid TwinID created using ed25519.
3. yggdrasil service running with a valid ip assigned to the twin on polkadot.
4. Golang compiler > 1.13 to run the grid proxy server.

## Endpoints

### `/farms`

- Bring all nodes information and public ips

    Example

    ```json
    // 20210815123713
    // http://localhost:8080/farms

    {
      "data": {
        "farms": [
          {
            "name": "devnet",
            "farmId": 1,
            "twinId": 3,
            "version": 1,
            "cityId": 0,
            "countryId": 0,
            "pricingPolicyId": 1
          }
        ],
        "publicIps": [
          {
            "id": "kGoHpiNM1_R",
            "ip": "185.206.122.40/24",
            "farmId": "OubK0WQyJT",
            "contractId": 0,
            "gateway": "185.206.122.1"
          }
        ]
      }
    }
    ```

### `/nodes`

- Bring all nodes information and public configurations

    Example

    ```json
    // 20210815123555
    // http://localhost:8080/nodes

    {
      "data": {
        "nodes": [
          {
            "version": 1,
            "id": "LWeENXIU2a",
            "nodeId": 1,
            "farmId": 1,
            "twinId": 5,
            "countryId": 0,
            "gridVersion": 1,
            "cityId": 0,
            "uptime": 0,
            "created": 1628862798,
            "farmingPolicyId": 2,
            "cru": "24",
            "mru": "202875785216",
            "sru": "512110190592",
            "hru": "9001778946048"
          },
        ],
        "publicConfigs": [
          {
            "gw4": "185.206.122.1",
            "ipv4": "185.206.122.31/24",
            "ipv6": "2a10:b600:1:0:fc38:90ff:feb4:b15d/ 64",
            "gw6": "fe80::2e0:ecff:fe7b:7a67"
          }
        ]
      }
    }
    ```

### `/nodes/<node-id>`

- Bring the node active used and total resources

    Example

    ```json
    // 20210815123807
    // http://localhost:8080/nodes/1

    {
      "total": {
        "cru": 24,
        "sru": 512110190592,
        "hru": 9001778946048,
        "mru": 201863462912,
        "ipv4u": 0
      },
      "used": {
        "cru": 2,
        "sru": 126701535232,
        "hru": 0,
        "mru": 25548913455,
        "ipv4u": 0
      }
    }
    ```
