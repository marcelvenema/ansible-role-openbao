# Role: OpenBao Vault

<table style="border:0px; width:100%"><tr><td width=160px valign=top><img src="media/icon_openbao.png" alt="OpenBao icon" width=128 height=128></td>
<td>
Ansible role for installation, configuration, usage, and management of OpenBao Vault.<br>OpenBao Vault is a tool for securely accessing secrets. A secret is anything that you want to tightly control access to, such as API keys, passwords, certificates, and more. OpenBao Vault provides a unified interface to any secret while providing tight access control and recording a detailed audit log. OpenBao is an open source, community driven fork of Hashicorp Vault.<br>Official website: `https://openbao.org/`<br><br>
</td>
</tr></table>

Ansible role OpenBao : [Design](docs/DESIGN.md)  |  [Administration](docs/ADMINISTRATION.md)  |  [Examples](examples)  |  [Test](molecule)  |  [Issues]()  |<br>
<br>
Latest version: <kbd>v0.4.1</kbd> - See [RELEASES](docs/RELEASES.md) for more information.<br>

# Role variables
Available variables are listed below, along with default values (see `defaults/main.yml`):<br>


# Actions summary:

<table style="border:0px; width:100%">
  <tr><th><a href="#Deployment">Deployment</a></th><th><a href="#Secrets-Management">Secrets Management</a></th><th><a href="#Secret-Engines">Secret Engines</a></th><th><a href="#Policies">Policies</a></th><th><a href="#AppRoles">AppRoles</a></th><th><a href="#Administration">Administration</a></th></tr>
  <tr>
    <td valign=top>install<br>uninstall<br>update<br></td>
    <td valign=top>create_secret<br>destroy_secret<br>get_secret<br>import_secret<br>export_secret<br></td>
    <td valign=top>create_secret_engine<br>destroy_secret_engine<br></td>
    <td valign=top>create_policy<br>destroy_policy<br></td>
    <td valign=top>create_approle<br>destroy_approley<br></td>
    <td valign=top>configure<br>start<br>stop<br>unseal<br></td>
  </tr>
</table>

## Default variables:
This role uses the `openbao` variable for configuration parameters. See [defaults/main.yml](defaults/main.yml) for a comprehensive list of available options and their descriptions.<br>

## Actions

### Deployment

action: **install**<br>
_Installation of the latest version of OpenBao Vault_.<br>
This action will install the latest version of OpenBao Vault on the target hosts using the specified container image and configuration parameters. It ensures that the Vault service is set up and ready for use according to the provided variables.<br>
variables:<br>
<kbd>openbao - container - name</kbd> : (optional) Name of container. Default is 'openbao'.<br>
<kbd>openbao - container - repository_url</kbd> - URL with the location of the container repository. Can be a URL or path to a local or remote file, for example, 'docker.io/openbao/openbao', '/tmp/openbao.tar', 'https://192.168.1.1/repo/vault2.41.1.tar'. By default, it points to docker.io/openbao/openbao via defaults/main.yml.<br>
<kbd>openbao - container - repository_tag</kbd> : (optional) Release or version number of the image. Default is 'latest'.<br>
<kbd>openbao - container - repository_checksum</kbd> : (optional) Checksum of the container image. Example: "sha256:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef" or "1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef".<br>
<kbd>openbao - container - repository_checksum_algorithm</kbd> : (optional) Algorithm for the checksum, for example, sha256, sha512, md5, etc.<br>
<kbd>openbao - container - platform</kbd>  : (optional) Install on a specific platform, for example, podman, kubernetes, host. Default is podman-. (podman, kubernetes, host).<br>
<kbd>openbao - container - uninstall</kbd> : (optional) true/false. When true, uninstall is started before installation.<br>

```
- name: Install OpenBao Vault
    hosts: vault-server
    roles:
     - role: openbao
         vars:
             action: install
             openbao:
               container:
                 repository_url: docker.io/openbao/openbao

```


action: **uninstall**<br>
_Uninstallation of OpenBao Vault_.<br>
This action will remove the OpenBao Vault container from the target host, ensuring all associated services are stopped and the container is deleted. Use the `keep_data` variable to retain data folders if required.
variables:<br>
<kbd>keep_data (optional)</kbd> : true/false. When true, data folders are kept during uninstall. Default is false.<br>

```
- name: Uninstall OpenBao Vault
    hosts: vault-server
    roles:
     - role: openbao
         vars:
             action: uninstall
             keep_data: true
```


action: **update**<br>
_Update to the latest OpenBao Vault version_.<br>
This action will update the current OpenBao Vault server to a newer version. By default, it reads the `repository_url` configured in Vault and attempts to download and install the latest available version. If a specific `repository_url` is provided, the update will use that source instead. The update process ensures that the Vault service is upgraded safely, minimizing downtime and preserving existing configuration and data. Use this action to keep your OpenBao Vault deployment up to date with the latest features and security patches.
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_name</kbd> : unique identification of OpenBao instance, for example server name/cluster name. Will be used to get/put parameters in Vault.<br>
<kbd>openbao - container - repository_url</kbd> - (optional) URL with the location of the container repository. Can be a URL or path to a local or remote file, for example, 'docker.io/openbao/openbao', '/tmp/openbao.tar', 'https://192.168.1.1/repo/vault2.41.1.tar'. By default, it points to docker.io/openbao/openbao via defaults/main.yml.<br>
<kbd>openbao - container - repository_tag</kbd> : (optional) Release or version number of the image. Default is 'latest'.<br>
<kbd>openbao - container - repository_checksum</kbd> : (optional) Checksum of the container image. Example: "sha256:1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef" or "1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef".<br>
<kbd>openbao - container - repository_checksum_algorithm</kbd> : (optional) Algorithm for the checksum, for example, sha256, sha512, md5, etc.<br>

```
- name: Update OpenBao Vault
    hosts: vault-server
    roles:
     - role: openbao
         vars:
             action: update
             vault_address: http://localhost:8200
             vault_token: <token>
             secret_name: 10-233-0-101

or:

- name: Update OpenBao Vault
    hosts: vault-server
    roles:
     - role: openbao
         vars:
             action: update
             openbao:
               container:
                 repository_url: "https://<nexus repository>/repository/containers/openbao_2.4.1.tar"

```


## Secrets Management

action: **create_secret**<br>
_Create a secret in Vault_.<br>
This action will create a secret in OpenBao Vault. It securely stores sensitive information—such as passwords, API keys, or certificates—within the Vault instance. The secret is saved under the specified secret engine and name, using key-value pairs provided in the configuration. This ensures that only authorized users and applications can access or manage the secret, supporting secure automation and compliance requirements.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_engine_name</kbd> : name of secret engine.<br>
<kbd>secret_name</kbd> : unique identification of OpenBao instance, for example server name/cluster name. Will be used to get/put parameters in Vault.<br>
<kbd>secret_value</kbd> : Path where the secret will be stored.<br>
<kbd>secret_keyvalue</kbd> : Data of the secret in key-value pairs.<br>

```
- name: Create secret in Vault
    hosts: vault-server
    roles:
     - role: vault
         vars:
             action: create_secret
             vault_address: http://localhost:8200
             vault_token: <token>
             secret_engine_name: nexus-repository
             secret_name: 10-233-0-101
             secret_keyvalue: "{ "username":"administrator", "password":"password123"}

```

action: **destroy_secret**<br>
_Delete a secret from Vault_. `ROADMAP`<br>
This action will delete a secret from the Vault.
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_engine_name</kbd> : Path where the secret is stored.<br>
<kbd>secret_value</kbd> : Path where the secret will be stored.<br>

```
- name: Destroy secret from Vault
    hosts: vault-server
    roles:
     - role: vault
         vars:
             action: destroy_secret
             vault_address: http://localhost:8200
             vault_token: <token>
             secret_engine_name: nexus-repository
             secret_value: server-nexus
```


action: **get_secret**<br>
Get a secret from Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_engine_name</kbd> : Path where the secret is stored.<br>

```

```


action: **import_secrets**<br>
Import secret from file into Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_engine_name</kbd> : Path where the secret is stored.<br>

```

```


action: **export_secrets**<br>
Export secrets from Vault to file.<br>
This action will get secrets from the Vault and stores it into an encrypted file.<br>
Use `secret_engine_name` and `secret_name` for single secret values. Use `secrets` for multiple secret values.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_engine_name</kbd> : Path where the secret is stored.<br>
<kbd>secret_name</kbd> : Name of secret.<br>
<kbd>secrets</kbd> : Path where the secret is stored.<br>

```
- name: Export secrets from Vault
  hosts: localhost
  vars:
    vault_address: "{{ lookup('ansible.builtin.env', 'VAULT_ADDR', default=Undefined) }}"
    vault_token: "{{ lookup('ansible.builtin.env', 'VAULT_TOKEN', default=Undefined) }}"

  tasks:
  - name: Export secrets from Vault
    ansible.builtin.include_role:
      name: vault
    vars:
      action : export_secrets
      # vault_address : "" # set in environment variable
      # vault_token   : "" # set in environment variable
      # secret_engine_name : # set in secrets variable
      # secret_name        : # set in secrets variable
      filename : "secrets_export1"
      secrets  : |
        [
          {
            "secret_engine_name": "cisco-callmanager",
            "secret_name": "localhost-localdomain",
            "secret_data": ""
          },
          {
            "secret_engine_name": "hashicorp-vault",
            "secret_name": "localhost-localdomain",
            "secret_data": ""
          }]

```


## Secret Engines

action: **create_secret_engine**<br>
Create secret engine in Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>filename</kbd> : Path where the secret is stored.<br>

```
- name: Import secrets from Vault
  hosts: localhost
  vars:
    vault_address: "{{ lookup('ansible.builtin.env', 'VAULT_ADDR', default=Undefined) }}"
    vault_token: "{{ lookup('ansible.builtin.env', 'VAULT_TOKEN', default=Undefined) }}"

  tasks:
  - name: Import secrets from Vault
    ansible.builtin.include_role:
      name: vault
    vars:
      action : import_secrets
      # vault_address : "" # set in environment variable
      # vault_token   : "" # set in environment variable
      filename : "secrets_export1.zip"

```


action: **destroy_secret_engine**<br>
Destroy secret engine in Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>secret_engine_name</kbd> : Path where the secret is stored.<br>

```

```


## Policies

action: **create_policy**<br>
Create a policy in Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>policy_name</kbd> : Name of the policy.<br>
<kbd>policy_rules</kbd> : Rules of the policy.<br>

```
- name: Create policy in Vault
    hosts: vault-server
    roles:
     - role: vault
         vars:
             action: create_policy
             vault_address: http://localhost:8200
             vault_token: <token>
             policy_name: my-policy
             policy_rules: |
                 path "secret/*" {
                     capabilities = ["create", "read", "update", "delete", "list"]
                 }
```

action: **destroy_policy**<br>
Destroy a policy from Vault. `ROADMAP`<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>policy_name</kbd> : Name of the policy.<br>

```
- name: Destroy policy from Vault
    hosts: vault-server
    roles:
     - role: vault
         vars:
             action: delete_policy
             vault_address: http://localhost:8200
             vault_token: <token>
             policy_name: my-policy
```

## AppRoles

action: **create_approle**<br>
Create AppRole in Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>

```

```


action: **destroy_approle**<br>
Destroy AppRole in Vault.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to the Vault address, e.g., `http://localhost:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>

```

```

## Administration

action: **start**<br>
Start of HashiCorp Vault service.<br>
variables:<br>
<kbd>(none)</kbd> : No variables required.<br>

```
- name: Start HashiCorp Vault service
    hosts: vault-server
    roles:
     - role: vault
         vars:
             action: start
```

action: **stop**<br>
Stop of HashiCorp Vault service.<br>
variables:<br>
<kbd>(none)</kbd> : No variables required.<br>

```
- name: Stop HashiCorp Vault service
    hosts: vault-server
    roles:
     - role: vault
         vars:
             action: stop
```

action: **unseal**<br>
Unseal Vault to make it ready for use.<br>
variables:<br>
<kbd>vault_address</kbd> : URL to Vault, for example, `https://192.168.1.0:8200`.<br>
<kbd>vault_token</kbd> : Token for Vault access.<br>
<kbd>vault_unseal_keys</kbd> : Unseal keys of Vault. These are the keys generated during installation.<br>

```

```


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

## Installation
Installation Vault via action 'install'.<br>
Example for installing Vault:

```
- name: Install Vault
    hosts: vault-server
    tasks:
        - name: Install HashiCorp Vault
            ansible.builtin.include_role:
                name: vault
                vars:
                    action: install
                    vault:
                      container:
                        respository_url: "https://releases.hashicorp.com/vault/latest/vault_latest_linux_amd64.zip"
```

## Configuration
(none).<br>

## Other information

**Global variables**

# Create list of all variables used in /vars/main.yml


## License
MIT

## Author
Marcel Venema
