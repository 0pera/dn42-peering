# dn42-peering
config for peering with AS4242423077

# nodes info

| | us-1 | hk-1 | cn-1 |
|---|---|---|---|
|wireguard_public_key| 2SyET8eMECoQXCH+pRGASj4moNwlexrbXFzPDmex3SI= | aiJkoVGUNJvvBmZ0FPs/4VdfsSLVKgD9xBDvyYwuRFw= | KDhLOZRYKNxF5groQkc5xhx5TGjvyFOV0dTjVxdz2j4= |
|endpoint| us-1.dn42.ferrets.space | hk-1.dn42.ferrets.space | <hidden,contact me via email for more info> |
|endpoint port| 20000+<last 4 digits of you asn> | 20000+<last 4 digits of you asn> | 20000+<last 4 digits of you asn> |
|as_num| 4242423077 | 4242423077 | 4242423077 |
|ipv4_addr| 172.23.183.129 | 172.23.183.131 | 172.23.183.128 |
|ipv6_addr| fd48:fa31:502b:10::2(preferred) | fd48:fa31:502b:10::4(preferred) | fd48:fa31:502b:10::1(preferred) |
|ipv6_linklocal| fe80::3077(experimental) | fe80::3077(experimental) | fe80::3077(experimental) |
|mp_bgp| disabled | disabled | disabled |
|extend_nexthop| disabled | disabled | disabled |

# communities info
## infomation communities
communities listed below shall be transited across ASes, you should `keep` these communities when transiting prefixes to another AS.
| communities | description|
| --- | --- |
| 64511:41-70 | prefixes originated from, see https://dn42.eu/howto/BGP-communities |
| 64511:1000-1999 | prefixes originated from, see https://dn42.eu/howto/BGP-communities |

communities listed below shall `not` be transited across ASes, you should `delete` these communities when transiting prefixes to another AS.
| communities | description|
| --- | --- |
| 64511:1-39 | connection info communities are stripped, I'm not using this for route select|
| 4242423077:1:41-70 | prefixes are learned from dn42_region |
| 4242423077:1:1000-1999 | prefixes are learned from dn42_country |
| 4242423077:2:41-70 | prefixes that should `not` advertised to dn42_region |
| 4242423077:2:1000-1999 | prefixes that should `not` advertised to dn42_country |
| 4242423077:3:41-70 | prefixes that should `only` advertised to dn42_region |
| 4242423077:3:1000-1999 | prefixes that should `only` advertised to dn42_country |

## control communities
Communities below are supported, and will be processed.
| communities | description|
| --- | --- |
| blackhole | routes with blackhole community will be marked blackhole and traffic will be drop because rp_filter setto loose |
| no_export | routes with no-export community will not be exported to other ASes |
| no_advertise | routes with no-advertise community will not be advertise to other nodes of my network or other Peers |

# route policies
## received
1. only prefixes in 172.20.0.0/14 are accepted in ipv4 channel.
2. only rpki valid prefixes are accepted, invalid and unknown prefixes are rejected.
3. prefixes with as_path length >8 are rejected.

## transit
1. if a prefix is learned from AS1, it will not be advertised to AS1.
2. if a prefix is originated from AS1, it will not be advertised to AS1.
3. prefixes are not transited between CN and global.