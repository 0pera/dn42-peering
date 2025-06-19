# dn42-peering
config for peering with AS4242423077

# nodes info

| | us-1 | hk-1 |
|---|---|---|
|wireguard_public_key| 2SyET8eMECoQXCH+pRGASj4moNwlexrbXFzPDmex3SI= | aiJkoVGUNJvvBmZ0FPs/4VdfsSLVKgD9xBDvyYwuRFw= |
|endpoint| us-1.dn42.ferrets.space | hk-1.dn42.ferrets.space |
|endpoint port| 20000+<last 4 digits of you asn> | 20000+<last 4 digits of you asn> |
|as_num| 4242423077 | 4242423077 |
|ipv4_addr| 172.23.183.129 | 172.23.183.131 |
|ipv6_addr| fd48:fa31:502b:10::2 | fd48:fa31:502b:10::4 |
|mp_bgp| disabled | disabled |
|extend_nexthop| disabled | disabled |

# communities info
64511:1-39 connection info communities are stripped, I'm not using this for route select
64511:41-70 see https://dn42.eu/howto/BGP-communities
64511:1000-1999 see https://dn42.eu/howto/BGP-communities

4242423077:1:41-70 route is learn outside of my network, learning from dn42_region
4242423077:1:1000-1999 route is learn outside of my network, learning from dn42_country
