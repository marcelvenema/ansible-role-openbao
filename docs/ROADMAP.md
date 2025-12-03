# Vision and Roadmap

## Vision

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

***



## Roadmap



**Export and Import of secrets**
The export_secrets service from a secret engine to a JSON file and import_secrets for vice-versa needs to be made more robust so that it is production-ready.<br/>
**PKI certificates**
PKI certificates can be stored and issued in the Vault.

