# Groups endpoint examples

Use example requests to better understand how to work with groups in the node classifier API.

These requests assume the following configuration:

-   The Puppet master is running on `puppetlabs-nc.example.vm` with access to certificates and whitelisting to enable URL requests.
-   Port 4433 is open.

## Create a group called My Nodes

This request uses POST /v1/groups to create a group called *My Nodes*.

```
curl -X POST -H 'Content-Type: application/json' \
  --cert /etc/puppetlabs/puppet/ssl/certs/puppetlabs-nc.example.vm.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/puppetlabs-nc.example.vm.pem \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  -d '{ "name": "My Nodes",
        "parent": "00000000-0000-4000-8000-000000000000",
        "environment": "production",
        "classes": {}
      }' \
  https://puppetlabs-nc.example.vm:4433/classifier-api/v1/groups
```

**Related information**  


[POST /v1/groups](groups_endpoint.md#)

## Get the group ID of My Nodes

This request uses the groups endpoint to get details about groups.

```
curl 'https://puppetlabs-nc.example.vm:4433/classifier-api/v1/groups' \
   -H "Content-Type: application/json" \
   --cert /etc/puppetlabs/puppet/ssl/certs/puppetlabs-nc.example.vm.pem \
   --key /etc/puppetlabs/puppet/ssl/private_keys/puppetlabs-nc.example.vm.pem \
   --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem
```

The response is a JSON file containing details about all groups, including the *My Nodes* group ID.

```
{
  "environment_trumps": false,
  "parent": "00000000-0000-4000-8000-000000000000",
  "name": "My Nodes",
  "variables": {},
  "id": "085e2797-32f3-4920-9412-8e9decf4ef65",
  "environment": "production",
  "classes": {}
}
```

**Related information**  


[Groups endpoint](groups_endpoint.md#)

## Pin a node to the My Nodes group

This request uses POST /v1/groups/<id\> to pin the node *example-to-pin.example.vm* to *My Groups* using the group ID retrieved in the previous step.

```
 curl -X POST -H 'Content-Type: application/json' \
   --cert /etc/puppetlabs/puppet/ssl/certs/puppetlabs-nc.example.vm.pem \
   --key /etc/puppetlabs/puppet/ssl/private_keys/puppetlabs-nc.example.vm.pem \
   --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
   -d '{ "rule": ["or", ["=", "name", "example-to-pin.example.vm"]] }' \
        https://puppetlabs-nc.example.vm:4433/classifier-api/v1/groups/085e2797-32f3-4920-9412-8e9decf4ef65
```

**Related information**  


[POST /v1/groups/<id\>](groups_endpoint.md#)

## Pin a second node to the My Nodes group

This request uses POST /v1/groups/<id\> to pin a second node *example-to-pin-2.example.vm* to *My Groups*.

**Note:** You must supply all the nodes to pin to the group. For example, this request includes both *example-to-pin.example.vm* and *example-to-pin-2.example.vm*.

```
curl -X POST -H 'Content-Type: application/json' \
  --cert /etc/puppetlabs/puppet/ssl/certs/puppetlabs-nc.example.vm.pem.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/puppetlabs-nc.example.vm.pem.pem \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  -d '{ "rule": ["or", ["=", "name", "example-to-pin.example.vm"], ["=", "name",     "example-to-pin-2.example.vm"]] }' \
      https://puppetlabs-nc.example.vm.pem:4433/classifier-api/v1/groups/085e2797-32f3-4920-9412-8e9decf4ef65
```

**Related information**  


[POST /v1/groups/<id\>](groups_endpoint.md#)

## Add a class and parameters to the My Nodes group

This request uses POST /v1/groups/<id\> to specify the *apache* class and parameters for *My Groups*.

```
curl -X POST -H 'Content-Type: application/json' \
  --cert /etc/puppetlabs/puppet/ssl/certs/puppetlabs-nc.example.vm.pem.pem \
  --key /etc/puppetlabs/puppet/ssl/private_keys/puppetlabs-nc.example.vm.pem.pem \
  --cacert /etc/puppetlabs/puppet/ssl/certs/ca.pem \
  -d '{ "classes": {"apache": {"serveradmin": "roy@reynholm.co.uk","keepalive_timeout": null} } }' \
      https://puppetlabs-nc.example.vm.pem:4433/classifier-api/v1/groups/085e2797-32f3-4920-9412-8e9decf4ef65
```

**Related information**  


[POST /v1/groups/<id\>](groups_endpoint.md#)

