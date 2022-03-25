# AWS VPC Peering Connection

## Purpose

By default, VPCs don't allow traffic from anything outside the VPC. A `peering connection` is a network connection that allows traffic to be routed between VPCs using IPv4/6 addresses.

## Steps

1. Ensure `DNS hostnames` is enabled for both VPCs.
    - `DNS hostnames` - indicates whether instances with public IP addresses get corresponding public DNS hostnames.

2. Create the `VPC peering connection`.
    - Set acceptor and requester VPC ids.
    - `Edit DNS settings`
        - `Allow accepter VPC`
        - `Allow requester VPC`

3. Edit the `route tables` for both VPCs to allow traffic from the private IP addresses assigned to each VPC
    - Go to the route table of `VPC 1`
    - `Edit Routes`
    - Create new route with:
        - `Destination` = `IPv4 CIDR` of `VPC 2` (ex: `172.31.0.0/16`)
        - `Target` = `peering connection` just created
    - Do the same thing for the route table of `VPC 2` using the `IPv4 CIDR` of `VPC 1` as the `Destination`

4. For the `security groups` of the acceptor VPC, allow traffic from the `IPv4 CIDR` of the requestor VPC (ex: `172.31.0.0/16`)
