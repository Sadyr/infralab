## Role to configure network on virtualization node

### Variable to create bridge devices and connections to use for virtual machines

virt_network_bridges: type = list, elements of list = dictionary

```yml
virt_network_bridges:
  - name: <name for bridge device and connection> # Will be added prefix br- to device and connection name
    subnet:  

```

```yml
---
virt_network_bridges:
  - name: mgmt
    subnet: 10.10.2.0/24
    ip:
      - 10.10.2.1
  - name: int
    subnet: 10.10.4.0/24
    ip:
      - 10.10.4.1
  - name: ext
    subnet: 10.10.6.0/24
    ip:
      - 10.10.6.1

---
virt_network_bridges:
  - name: mgmt
    state: present
    ip4: 10.10.0.1/24

  - name: l2-fabric
    state: absent
    method4: disabled
    method6: disabled

  - name: int
    state: absent
    method6: disabled
    method4: disabled

  - name: ext
    state: absent
    ip4: "{{ ext_gateway }}"

```
