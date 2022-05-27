# ansible-role-asdf

An Ansible role to configure [asdf] using [Bash & Git].

## Requirements

This role is only capable of installing asdf under bash.

## Role Variables

<table>
<tr>
<th>Variable</th>
<th>Default</th>
<th>Example</th>
</tr>
<tr>
<td>asdf_install</td>
<td>true</td>
<td>false</td>
</tr>
<tr>
<td>asdf_version</td>
<td>master</td>
<td>v0.10.0</td>
</tr>
<tr>
<td>asdf_plugins</td>
<td>[ ]</td>
<td>

```yaml
asdf_plugins:
  - name: nodejs
    state: present
    url: https://github.com/asdf-vm/asdf-nodejs.git
  - name: python
    state: present
```

</td>
</tr>
<tr>
<td>asdf_packages</td>
<td>[ ]</td>
<td>

```yaml
asdf_packages:
  - name: nodejs
    state: present
    version: latest
  - name: python
    state: present
    version: latest
```

</td>
</tr>
</table>

### Variable Notes

To configure asdf without installing asdf core, `asdf_install` can be set to `false`.

Where `state` is defined in each role variable, the default value is `present`, and can be omitted. If `state` is set to `absent`, the corresponding item will be removed.

## Example Playbook

```yaml
# Configure asdf

---

- name: Configure asdf
  hosts: workstations
  roles:
    - role: interdependence.asdf
      vars:
        asdf_version: v0.10.0
        asdf_plugins:
          - name: nodejs
            state: present
            url: https://github.com/asdf-vm/asdf-nodejs.git
          - name: python
            state: present
        asdf_packages:
          - name: nodejs
            state: present
            version: latest
          - name: python
            state: present
            version: latest
```

[asdf]: https://asdf-vm.com/
[Bash & Git]: https://asdf-vm.com/guide/getting-started.html
