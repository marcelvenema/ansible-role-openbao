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

<table style="border:0px; width:100%">
  <tr>
  <th><a href="#administration">administration</a></th><th><a href="#approles">approles</a></th><th><a href="#deployment">deployment</a></th><th><a href="#policies">policies</a></th><th><a href="#secret_engines">secret_engines</a></th><th><a href="#secrets">secrets</a></th>
  </tr>
  <tr><td valign=top>start<br>stop<br>unseal<br></td><td valign=top>create_approle<br>destroy_approle<br>get_approle<br></td><td valign=top>configure<br>install<br>uninstall<br>update<br></td><td valign=top>create_policy<br>destroy_policy<br>get_policy<br></td><td valign=top>create_secret_engine<br>destroy_secret_engine<br>get_secret_engine<br></td><td valign=top>create_secret<br>destroy_secret<br>export_secrets<br>get_secret<br>import_secrets<br></td></tr>
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
