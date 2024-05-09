Cybersecurity deals with the protection of computers from information theft, or damage. To counter possible intruders from the [[Internet|internet]] security mechanisms are used. These security mechanisms commonly includes [[Cryptography|cryptography]].

Security protocols are used to protect information on the internet. Some common security protocols include:
- **Security Socket Layer** (SSL)
- **Transport Layer Security** (IETF)

Both of these protocols are used to establish a shared key to protect messages using symmetric encryption. These protocols have a sub-protocol of a TLS handshake which negotiates parameters, TLS Record which is the actual secure transport protocol, and a TLS Alert which closes the session.

**Diffie-Hellman Key Exchange** is the process used to establish the keys between two clients. This protocol doesn't originally provide authentication so digital signatures are used to exchange values. The equation used follows:
$$A=g^a\bmod p$$
Where $A$ is the private key, $g$ is the agreed upon generator, $p$ is a agreed upon prime, and $a$ is the private exponent. After this private key is calculated the public key is found by:
$$S=A^b \bmod p$$
Where $b$ is the secret exponent of the other person.

**Certificates** provide additional information for public keys, the matching private key, validity, and other parameters. Certificates can lead to private keys being compromised, resulting in certificates being revoked.

# VPN
**Virtual Private Network** logically connects a client to a network via an encrypted channel. This encryption works by giving the server they're connecting to a different IP address. This routes all packets through different networks as to provide protection. VPNs offer the benefits of being able to circumvent blocking and allows secured connection to servers.

# Intrusion Detection
There are two protocols used to stop malicious agents on a network. The first is **Intrusion Detection System** (IDS) which monitors the network for potential malicious activity. The second is **Intrusion Prevention System** (IPS) which is an IDS with the ability to block malicious activity. This detection is done through detecting specific attacks or known malware. Prevention methods commonly include dropping and blocking packets. Both systems are **anomaly-based** and **signature-based**, where the anomaly detects previously unknown attacks as opposed to the signature which searches for common attacks.

# Firewall
A firewall is a barrier between an internal and external network. It filters traffic according to the security rules of the network. In general all external traffic should be blocked unless stated otherwise. A **packet firewall** checks the IP address, protocols used, ports and current stage of connection. Packet firewalls are fast and cost efficient however are vulnerable to address spoofing, doesn't check application processes, attacks from inside the network and many more common attacks. Firewalls have the general disadvantage of policy rules becoming too complex and leading to slowdown.

# Access Control
Access control are the measures used to stop unwanted users from interfacing with important information. Some common access control methods are:
- **Passwords** are a common form of access control that is dependent on the user.
- **Biometrics** are easily usable however can easily be faked and are expensive to produce.

# Attacks
Within cybersecurity there are multiple types of attacks that are used by malicious users to gain access to a system. Some common ones include:
- **Phishing** is done by creating a fake website that causes a user to enter personal information.
- **Ransomware** installs malicious software that demands a payment under a threat.
- **Botnet** is a series of automatic processes called bots that connect to multiple devices and control them.
- **Denial of Service** (DOS) is an attack that prevents a service from working from the inside through
- **Malware** is any software that is harmful to a computer. It can be further subdivided by:
	- **Virus** which inserts itself into a program and runs itself, spreading throughout the device.
	- **Worm** is a standalone virus which tricks a user in using it.
	- **Trojan** is a piece of malware hidden in legitimate software.
