# Append the following aliases to ~/.zshrc or ~/.bashrc

## Openvpn alias

``
alias htb="sudo openvpn ~/Downloads/your_openvpn_path"
``

## Append a new domain to etc/hosts

``

addHost() {
    if [ $# -ne 2 ]; then
        echo "Usage: addhost <ip> <domain>"
        return 1
    fi

    ip="$1"
    domain="$2"

    # Check if the entry already exists in /etc/hosts
    if grep -q "$domain" /etc/hosts; then
        echo "$domain already exists in /etc/hosts."
    else
        echo "Adding $domain to /etc/hosts"
        sudo sed -i "1i$ip  $domain" /etc/hosts
    fi
}

``

## Examples

`htb`
`add host htb_ip htb_domain`
