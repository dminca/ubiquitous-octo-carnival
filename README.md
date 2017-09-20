# Ansible 2.4.0 bug test
> For testing an Ansible Vault bug

The bug is related to Ansible's incapability to parse the decrypted Ansible Vault variable in order to apply the `length()` function on it.

Ansible is throwing the following error after decrypting the FOO Ansible Vaulted variable and applying the `length(str)` function on it:

```sh
# in the jinja2 template, given this statement
{% if GOCD_AUTO_REGISTER_KEY | length > 0 %}

# throwing this error
object of type 'AnsibleVaultEncryptedUnicode' has no len()
```
