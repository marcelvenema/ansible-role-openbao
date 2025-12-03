<!-- DOCSIBLE START -->
# Role: OpenBao Vault


<table border="0">
  <tr>
    <td width="160px" valign="top"><img src="docs/media/icon_openbao.png" align="left" height="128" width="128" /></td>
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

# Action_type summary:

<table style="border:0px; width:100%">
  <tr>
  <th><a href="#administration">administration</a></th><th><a href="#approles">approles</a></th><th><a href="#deployment">deployment</a></th><th><a href="#policies">policies</a></th><th><a href="#secret_engines">secret_engines</a></th><th><a href="#secrets">secrets</a></th>
  </tr>
  <tr><td valign=top><a href="#start">start</a><br><a href="#stop">stop</a><br><a href="#unseal">unseal</a><br></td><td valign=top><a href="#create_approle">create_approle</a><br><a href="#destroy_approle">destroy_approle</a><br><a href="#get_approle">get_approle</a><br></td><td valign=top><a href="#configure">configure</a><br><a href="#install">install</a><br><a href="#uninstall">uninstall</a><br><a href="#update">update</a><br></td><td valign=top><a href="#create_policy">create_policy</a><br><a href="#destroy_policy">destroy_policy</a><br><a href="#get_policy">get_policy</a><br></td><td valign=top><a href="#create_secret_engine">create_secret_engine</a><br><a href="#destroy_secret_engine">destroy_secret_engine</a><br><a href="#get_secret_engine">get_secret_engine</a><br></td><td valign=top><a href="#create_secret">create_secret</a><br><a href="#destroy_secret">destroy_secret</a><br><a href="#export_secrets">export_secrets</a><br><a href="#get_secret">get_secret</a><br><a href="#import_secrets">import_secrets</a><br></td></tr>
</table>

Explanation of action variables in [`docs/index.md`](docs/index.md)<br>

***

- **changelog**<br>
    Change log.
    See [changelog](CHANGELOG.md)<br>

- **roadmap**<br>
    Vision and future developments.
    See [roadmap](docs/ROADMAP.md)<br>

***

## Preparations
(none).<br>

## Dependencies
Dependencies are listed in the **requirements.yml** file. Use `ansible-galaxy install -r requirements.yml --force` for installation.<br>
If this role is used in other playbooks or Ansible projects, the URL of this role must be added to the `requirements.yml` file. Using the above command, the role will be placed in the correct folder structure.<br>
<br>


## Example
Install OpenBao Vault:<br>
```ansible
- name: Install Openbao Vault
  hosts: vault-server
  vars:  
    openbao_container_repository_url: "http://192.168.1.1/repository/openbao"
  roles:
    - openbao
  
```


## Other information
(none)

## License
MIT

## Author
Marcel Venema
<!-- DOCSIBLE END -->
