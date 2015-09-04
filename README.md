[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# ansible-role-cloudhealth

## Requirements

This module requires `httplib2` to be installed on the host machine. It can be
installed via `apt-get` (`sudo apt-get install python-httplib2`) or via `pip`
(`sudo pip install httplib2`) if not available in the distribution package
manager.

## Role Variables

### `cloudhealth_api_key`

<img src="docs/cht_api_key.png" alt="CHT API Key" align="right" height="130px">

The `cloudhealth_api_key` is used to identify yourself to our API. This
variable is **required**.

Your API key can be found in the *Settings* section of
[your profile](https://apps.cloudhealthtech.com/profile). If it appears to be
empty, click on *Get API Key* to get one.

Define it in your playbooks like this:

```yaml
cloudhealth_api_key: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```
