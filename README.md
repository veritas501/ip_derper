# ip-derper

1. build

```
docker build . -t ip_derper
```

2. run

```
docker run --rm -d -p 50443:443 -p 3478:3478/udp ip_derper
```

3. modify tailscale ACLs

inserts this into tailscale ACLs: https://login.tailscale.com/admin/acls
```json
"derpMap": {
    "Regions": {
        "900": {
            "RegionID": 900,
            "RegionCode": "my_private_derper",
            "Nodes": [
                {
                    "Name": "1",
                    "RegionID": 900,
                    "HostName": "YOUR_SERVER_IP",
                    "IPv4": "YOUR_SERVER_IP",
                    "InsecureForTests": true,
                    "DERPPort": 50443
                }
            ]
        }
    }
}
```

enjoy :)