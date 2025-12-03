<!-- DOCSIBLE START -->
# Role: OpenBao Vault


<table border="0">
  <tr>
    <td width="160px" valign="top"><img src="media/icon_openbao.png" align="left" height="128" width="128" /></td>
    <td><b>Ansible role for OpenBao Vault</b><br/>
        Ansible role for installation, configuration, usage, and management of OpenBao Vault.<br>OpenBao Vault is a tool for securely accessing secrets. A secret
is anything that you want to tightly control access to, such as API keys, passwords, certificates, and more. OpenBao Vault provides a unified interface
to any secret while providing tight access control and recording a detailed audit log. OpenBao is an open source, community driven fork of Hashicorp
Vault.<br>Official website: `https://openbao.org/`<br><br>
        <br>
    </td>
  </tr>
</table>

Ansible role **Openbao** : [Design](DESIGN.md)  |  [Administration](ADMINISTRATION.md)  |  [Examples](../examples)  |  [Test](../molecule)  |  [Issues]()  |<br>
<br>
Latest version: <kbd>TBD</kbd> - See [CHANGELOG](CHANGELOG.md) for more information.<br>

***

# Role variables
Available variables are listed in defaults, see [`defaults/main.yml`](defaults/main.yml)<br>

***

# Action_type summary:

<table style="border:0px; width:100%">
  <tr>
  <th><a href="#administration">administration</a></th><th><a href="#approles">approles</a></th><th><a href="#deployment">deployment</a></th><th><a href="#policies">policies</a></th><th><a href="#secret_engines">secret_engines</a></th><th><a href="#secrets">secrets</a></th>
  </tr>
  <tr><td valign=top><a href="#start">start</a><br><a href="#stop">stop</a><br><a href="#unseal">unseal</a><br></td><td valign=top><a href="#create_approle">create_approle</a><br><a href="#destroy_approle">destroy_approle</a><br><a href="#get_approle">get_approle</a><br></td><td valign=top><a href="#configure">configure</a><br><a href="#install">install</a><br><a href="#uninstall">uninstall</a><br><a href="#update">update</a><br></td><td valign=top><a href="#create_policy">create_policy</a><br><a href="#destroy_policy">destroy_policy</a><br><a href="#get_policy">get_policy</a><br></td><td valign=top><a href="#create_secret_engine">create_secret_engine</a><br><a href="#destroy_secret_engine">destroy_secret_engine</a><br><a href="#get_secret_engine">get_secret_engine</a><br></td><td valign=top><a href="#create_secret">create_secret</a><br><a href="#destroy_secret">destroy_secret</a><br><a href="#export_secrets">export_secrets</a><br><a href="#get_secret">get_secret</a><br><a href="#import_secrets">import_secrets</a><br></td></tr>
</table>


# Actions

## administration category: <a id="administration"></a>

### start
action: **start**
Start OpenBao container.
variables:
<kbd>(none).</kbd><br>

### stop
action: **stop**
Stop OpenBao container.
variables:
<kbd>(none).</kbd><br>

### unseal
action: **unseal**
Unseal OpenBao Vault.
variables:
<kbd>vault_address</kbd>:  URL to Vault, for example `https://. Default value: (none).<br>
<kbd>vault_unseal_keys</kbd>:  Unseal keys. Default value: (none).<br>
<br>


## approles category: <a id="approles"></a>

### create_approle
action: **create_approle**
Create an approle.
variables:
<kbd>(none).</kbd><br>

### destroy_approle
action: **destroy_approle**
Remove an approle.
variables:
<kbd>(none).</kbd><br>

### get_approle
action: **get_approle**
Retrieve the configuration of an approle.
variables:
<kbd>(none).</kbd><br>


## deployment category: <a id="deployment"></a>

### configure
action: **configure**
Configure OpenBao. Create a token and unseal keys. Unseal OpenBao.
variables:
<kbd>(none).</kbd><br>

### install
action: **install**
Installation of the latest version of OpenBao. Basic configuration.
variables:
<kbd>uninstall</kbd>(optional):  Start uninstallation before installation begins. true/false. Default is 'true'.. Default value: true<br>
<br>

### uninstall
action: **uninstall**
Uninstallation of OpenBao. Removes the container, files, users, and groups.
variables:
<kbd>(none).</kbd><br>

### update
action: **update**
Update OpenBao to the latest version.
variables:
<kbd>(none).</kbd><br>


## policies category: <a id="policies"></a>

### create_policy
action: **create_policy**
Create a policy.
variables:
<kbd>(none).</kbd><br>

### destroy_policy
action: **destroy_policy**
Remove a policy.
variables:
<kbd>(none).</kbd><br>

### get_policy
action: **get_policy**
Retrieve the configuration of a policy.
variables:
<kbd>(none).</kbd><br>


## secret_engines category: <a id="secret_engines"></a>

### create_secret_engine
action: **create_secret_engine**
Create a secret engine.
variables:
<kbd>(none).</kbd><br>

### destroy_secret_engine
action: **destroy_secret_engine**
Remove a secret engine.
variables:
<kbd>(none).</kbd><br>

### get_secret_engine
action: **get_secret_engine**
Retrieve the configuration of a secret engine.
variables:
<kbd>(none).</kbd><br>


## secrets category: <a id="secrets"></a>

### create_secret
action: **create_secret**
Create a secret.
variables:
<kbd>(none).</kbd><br>

### destroy_secret
action: **destroy_secret**
Remove a secret.
variables:
<kbd>(none).</kbd><br>

### export_secrets
action: **export_secrets**
Export a secret from Vault.
variables:
<kbd>vault_address</kbd>:  URL to Vault, for example `https://192.168.1.0:8200`.. Default value: (none).<br>
<kbd>vault_token</kbd>:  Token for access to Vault.. Default value: (none).<br>
<br>

### get_secret
action: **get_secret**
Retrieve a secret.
variables:
<kbd>(none).</kbd><br>

### import_secrets
action: **import_secrets**
Import a secret into Vault.
variables:
<kbd>vault_address</kbd>:  URL to Vault, for example `https://192.168.1.0:8200`.. Default value: (none).<br>
<kbd>vault_token</kbd>:  Token for access to Vault.. Default value: (none).<br>
<br>


<!-- DOCSIBLE END -->
