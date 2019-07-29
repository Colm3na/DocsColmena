# DAppNodePackage-Cosmos 

[![Website dappnode.io](https://img.shields.io/badge/Website-dappnode.io-brightgreen.svg)](https://dappnode.io/)
[![Documentation Wiki](https://img.shields.io/badge/Documentation-Wiki-brightgreen.svg)](https://docs.dappnode.io)
[![RIOT DAppNode](https://img.shields.io/badge/RIOT-DAppNode-blue.svg)](https://riot.dappnode.io)
[![Twitter Follow](https://img.shields.io/twitter/follow/espadrine.svg?style=social&label=Follow)](https://twitter.com/dappnode)


<h1 align="center"> <a href="https://github.com/cosmos/gaia/blob/master/docs/join-mainnet.md">Cosmos Network fullnode</a> and <a href="https://github.com/luniehq/lunie">Lunie web Wallet </a> for DAppNode </h1>

[DAppNode](https://github.com/dappnode/DAppNode) is a web application and also the name of the [hardware](https://shop.dappnode.io) of an amazing project.
Its goal is to make it extremely easy to install and run blockchain applications, full nodes and help to decentralice the nodes.

What we have develop here is the DAppNode package that inclues a complete Cosmos Full Node
and its official web wallet, Lunie.
With this package you can have your own Cosmos full node and host your own clone of Lunie right at home.

> The build process of the package is based on [dappnode-sdk](https://github.com/dappnode/DAppNodeSDK)

> Latest version of the package (**0.1.1**) maintained by [La ColmenaSvQ](https://github.com/Colm3na)

> [Manifest.](dappnode_package.json)



<h1 align="center"> You can install it in your DAppnode with: </h1>


<sumary>
<h2 align="center"> IPFS hash: </h2>
</sumary>
<details>
/ipfs/QmQetWYatxuuJCBA8MAVxnEc6AQW9XFza9H1hCs5QXw3WF
</details>
  
<sumary>
<h2 align="center"> DAppNode link: </h2>
</sumary>
<details>
  
http://my.dappnode/#/installer/cosmos.public.dappnode.eth
</details>

<sumary>
<h2 align="center"> If you need a peer for IPFS you can add the node of Colm3na (in your DAppNode): </h2>
</sumary>

<details>
http://my.dappnode/#/system/add-ipfs-peer/%2Fdns4%2F06f904705c1cde31.dyndns.dappnode.io%2Ftcp%2F4001%2Fipfs%2FQme3qzA1X2q1agL7rpmej6dS5ygGyyL9obeZ8mCD6KkPQt
</details>

## Getting Started

With these instructions you can install a Cosmos node in DAppNode and use [Lunie](https://github.com/luniehq/lunie) with [Ledger.](https://www.ledger.com)

### Prerequisites

<sumary>
- If you are using Linux you need to follow these steps for the connection issues(described on the <a href="https://support.ledger.com/hc/en-us/articles/115005165269-Fix-connection-issues"> Ledger website.</a>)
</sumary>
<details>
<h3>1. Setup</h3>
<ul>
<li>Check if the plugdev group exists by entering the command:<br />
<pre><code>cat /etc/group | grep plugdev</code></pre>
</li>
<li><strong>Follow the steps below </strong><strong>if the previous command did not return </strong><strong>a result</strong>
<ol>
<li><strong>C</strong>reate the <strong>plugdev</strong> group:<br />
<pre><code>sudo groupadd plugdev</code></pre>
</li>
<li>Check if you are in the group <strong>plugdev</strong> with the command:
<pre><code>groups</code></pre>
</li>
<li>
<p>If the output does not contain <strong>plugdev</strong>, you are not in the <strong>plugdev </strong>group. Enter the command:</p>
<pre><code>sudo gpasswd -a &lt;user&gt; plugdev</code></pre>
<p><strong>Note</strong>: replace &lt;user&gt; by your username, e.g for user "mike", it would be: <strong>sudo gpasswd -a mike plugdev</strong>.</p>
</li>
<li>
<p>Logout and login for the change to take effect. To verify you are now in the <strong>plugdev</strong> group, enter:</p>
<pre><code>groups</code></pre>
and search for a <strong>plugdev</strong> occurrence. If it's not there, you've missed a step and should restart from step 1.</li>
</ol>
</li>
</ul>
<h3>2. Add the udev rules</h3>
<ol>
<li>Enter the following command to automatically add the rules and reload udev:
<pre><code>wget -q -O - https://raw.githubusercontent.com/LedgerHQ/udev-rules/master/add_udev_rules.sh | sudo bash</code></pre>
</li>
</ol>
</details>

- You need your own [DAppNode](https://github.com/dappnode/DAppNode).

- In your DAppNode install the package with:

```
http://my.dappnode/#/installer/cosmos.public.dappnode.eth
```

- Then you can go to the URL of your node, which would be something like this:

```
https://cosmos.public.dappnode/lunie
```

- By placing the mouse at the bottom right above `Cosmoshub-2` you can see that you are connected to your own Cosmos node.
> You're connected to cosmoshub-2 via https://cosmos.public.dappnode

> The first time we access the URL, warns us of the certificate, to be self-signed warns us of it as an error, we must accept it

## Contributing

Please read [CONTRIBUTING.md](https://github.com/dappnode/DAppNode/blob/master/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

## Authors

- **Fredy** - [DerFredy](https://github.com/derfredy)

- **Wimel** - [wimel](https://github.com/wimel)

## License 

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details
