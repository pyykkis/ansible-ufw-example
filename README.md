# Ansible ufw example

## Setup

    git clone git@github.com/pyykkis/ansible-ufw-example
    cd ansible-ufw-example
    vagrant up

## Discussion

In this example, ansible and vagrant is used to provision precise64 box. Ansible sets up following services

- ufw
  - `reject` as a default policy
  - allow/22 for OpenSSH
- nginx
  - ports 80 and 443 are rejected by ufw as no allow rule is specified for them

Firewall settings can be explored from host machine using [nmap](http://nmap.org/), or simply by
`curl 192.168.0.2`.

More information about UFW in general and Ansible ufw module in particular can be found from [Ubuntu UncomplicatedFirewall documentation](https://wiki.ubuntu.com/UncomplicatedFirewall) and [Ansible UFW module documentation](http://docs.ansible.com/ufw_module.html)

Using `reject` as a default policy is recommended by multiple sources, as `drop` doesn't really help with security,
and is a major PITA when debugging distributed systems [1], [2].

References:

[1]: [Why Firewall Reject Rules Are Better Than Firewall Drop Rules](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)
[2]: [Drop versus Reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)
