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

## administration: <a id="administration"></a>

### start <a id="start"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>start</b><br/>Start OpenBao container.<br></td>
  </tr>
</table>




action: **start**<br>
Start OpenBao container.<br>
variables:<br>
<kbd>(none).</kbd><br>

### stop <a id="stop"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>stop</b><br/>Stop OpenBao container.<br></td>
  </tr>
</table>




action: **stop**<br>
Stop OpenBao container.<br>
variables:<br>
<kbd>(none).</kbd><br>

### unseal <a id="unseal"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>unseal</b><br/>Unseal OpenBao Vault.<br></td>
  </tr>
</table>




action: **unseal**<br>
Unseal OpenBao Vault.<br>
variables:<br>
<kbd>vault_address</kbd>:  URL to Vault, for example `https://. Default value: (none).<br>
<kbd>vault_unseal_keys</kbd>:  Unseal keys. Default value: (none).<br>
<br>


## approles: <a id="approles"></a>

### create_approle <a id="create_approle"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>create_approle</b><br/>Create an approle.<br></td>
  </tr>
</table>




action: **create_approle**<br>
Create an approle.<br>
variables:<br>
<kbd>(none).</kbd><br>

### destroy_approle <a id="destroy_approle"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>destroy_approle</b><br/>Remove an approle.<br></td>
  </tr>
</table>




action: **destroy_approle**<br>
Remove an approle.<br>
variables:<br>
<kbd>(none).</kbd><br>

### get_approle <a id="get_approle"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>get_approle</b><br/>Retrieve the configuration of an approle.<br></td>
  </tr>
</table>




action: **get_approle**<br>
Retrieve the configuration of an approle.<br>
variables:<br>
<kbd>(none).</kbd><br>


## deployment: <a id="deployment"></a>

### configure <a id="configure"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>configure</b><br/>Configure OpenBao. Create a token and unseal keys. Unseal OpenBao.<br></td>
  </tr>
</table>




action: **configure**<br>
Configure OpenBao. Create a token and unseal keys. Unseal OpenBao.<br>
variables:<br>
<kbd>(none).</kbd><br>

### install <a id="install"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>install</b><br/>Installation of the latest version of OpenBao. Basic configuration.<br></td>
  </tr>
</table>




action: **install**<br>
Installation of the latest version of OpenBao. Basic configuration.<br>
variables:<br>
<kbd>uninstall</kbd>(optional):  Start uninstallation before installation begins. true/false. Default is 'true'.. Default value: true<br>
<br>

### uninstall <a id="uninstall"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>uninstall</b><br/>Uninstallation of OpenBao. Removes the container, files, users, and groups.<br></td>
  </tr>
</table>




action: **uninstall**<br>
Uninstallation of OpenBao. Removes the container, files, users, and groups.<br>
variables:<br>
<kbd>(none).</kbd><br>

### update <a id="update"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>update</b><br/>Update OpenBao to the latest version.<br></td>
  </tr>
</table>




action: **update**<br>
Update OpenBao to the latest version.<br>
variables:<br>
<kbd>(none).</kbd><br>


## policies: <a id="policies"></a>

### create_policy <a id="create_policy"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>create_policy</b><br/>Create a policy.<br></td>
  </tr>
</table>




action: **create_policy**<br>
Create a policy.<br>
variables:<br>
<kbd>(none).</kbd><br>

### destroy_policy <a id="destroy_policy"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>destroy_policy</b><br/>Remove a policy.<br></td>
  </tr>
</table>




action: **destroy_policy**<br>
Remove a policy.<br>
variables:<br>
<kbd>(none).</kbd><br>

### get_policy <a id="get_policy"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>get_policy</b><br/>Retrieve the configuration of a policy.<br></td>
  </tr>
</table>




action: **get_policy**<br>
Retrieve the configuration of a policy.<br>
variables:<br>
<kbd>(none).</kbd><br>


## secret_engines: <a id="secret_engines"></a>

### create_secret_engine <a id="create_secret_engine"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>create_secret_engine</b><br/>Create a secret engine.<br></td>
  </tr>
</table>




action: **create_secret_engine**<br>
Create a secret engine.<br>
variables:<br>
<kbd>(none).</kbd><br>

### destroy_secret_engine <a id="destroy_secret_engine"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>destroy_secret_engine</b><br/>Remove a secret engine.<br></td>
  </tr>
</table>




action: **destroy_secret_engine**<br>
Remove a secret engine.<br>
variables:<br>
<kbd>(none).</kbd><br>

### get_secret_engine <a id="get_secret_engine"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>get_secret_engine</b><br/>Retrieve the configuration of a secret engine.<br></td>
  </tr>
</table>




action: **get_secret_engine**<br>
Retrieve the configuration of a secret engine.<br>
variables:<br>
<kbd>(none).</kbd><br>


## secrets: <a id="secrets"></a>

### create_secret <a id="create_secret"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>create_secret</b><br/>Create a secret.<br></td>
  </tr>
</table>




action: **create_secret**<br>
Create a secret.<br>
variables:<br>
<kbd>(none).</kbd><br>

### destroy_secret <a id="destroy_secret"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>destroy_secret</b><br/>Remove a secret.<br></td>
  </tr>
</table>




action: **destroy_secret**<br>
Remove a secret.<br>
variables:<br>
<kbd>(none).</kbd><br>

### export_secrets <a id="export_secrets"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>export_secrets</b><br/>Export a secret from Vault.<br></td>
  </tr>
</table>




action: **export_secrets**<br>
Export a secret from Vault.<br>
variables:<br>
<kbd>vault_address</kbd>:  URL to Vault, for example `https://192.168.1.0:8200`.. Default value: (none).<br>
<kbd>vault_token</kbd>:  Token for access to Vault.. Default value: (none).<br>
<br>

### get_secret <a id="get_secret"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>get_secret</b><br/>Retrieve a secret.<br></td>
  </tr>
</table>




action: **get_secret**<br>
Retrieve a secret.<br>
variables:<br>
<kbd>(none).</kbd><br>

### import_secrets <a id="import_secrets"></a>
<table border="0">
  <tr>
    <td width="80px" valign="top"><img src="media/icon_openbao.png" align="left" height="64" width="64" /></td>
    <td>action: <b>import_secrets</b><br/>Import a secret into Vault.<br></td>
  </tr>
</table>




action: **import_secrets**<br>
Import a secret into Vault.<br>
variables:<br>
<kbd>vault_address</kbd>:  URL to Vault, for example `https://192.168.1.0:8200`.. Default value: (none).<br>
<kbd>vault_token</kbd>:  Token for access to Vault.. Default value: (none).<br>
<br>


<!-- DOCSIBLE END -->
