Ansible Role: Swap
=========

When swap is enabled, the operating system can use it as a temporary storage area to offload less frequently accessed memory pages from RAM, making room for more active processes. This helps prevent memory exhaustion and allows the system to handle a larger workload.

Requirements
------------

This Ansible role has been developed and thoroughly tested with Ansible Core version 2.15.0.

This role was designed for:

- CentOS 8 Stream
- RHEL 8

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

The "swap_enabled" variable is a boolean flag indicating whether swap space is enabled or disabled on the system.

    swap_enabled: true

To check if a swap file exists and provide a list of possible swap paths.

    swap_files:
      - /swap
      - /swapfile
      - /swap.img

The size of the swap space to create, the recommended swap size:

- If your system has less than 2GB of RAM: Allocate swap space that is equal to the amount of RAM or slightly more (e.g., 2GB).
- If your system has 2GB to 8GB of RAM: Allocate swap space that is equal to the amount of RAM or up to twice the amount of RAM.
- If your system has more than 8GB of RAM: Allocate swap space that is at least 4GB, and you can consider allocating less than twice the amount of RAM (e.g., 8GB of RAM with 4GB of swap space).
```
swap_size: '4096'
```

Specifies the file path of the swap file.

    swap_file_path: /swapfile
    
Set the swappiness, 30 is default, the recommended swappiness value is typically set to a value of 10.

    swappiness_value: 10

Set the vfs_cache_pressure, 100 is default, the recommended value for vfs_cache_pressure is typically set to a value of 50. 

    vfs_cache_pressure_value: 50
    
Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      become: true
      vars:
        swap_enabled: true
        swap_files:
          - /swap
          - /swapfile
          - /swap.img
        swap_size: '4096'
        swap_file_path: /swapfile
        swappiness_value: 10
        vfs_cache_pressure_value: 50
      roles:
        - ansible-role-swap

License
-------

MIT / BSD

Author Information
------------------

* Author: Jody WAN
* Linkedin: https://www.linkedin.com/in/jodywan/
* Website: https://www.jodywan.com
