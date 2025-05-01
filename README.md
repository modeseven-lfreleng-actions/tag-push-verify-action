<!--
# SPDX-License-Identifier: Apache-2.0
# SPDX-FileCopyrightText: 2025 The Linux Foundation
-->

# 🏷️ Verify Pushed Tag

Verifies the action/workflow event trigger was a tag push event.

Optionally, checks tag compliance with a given versioning type.

## tag-push-verify-action

## Supported Versioning Types

Checks the pushed tag against these versioning types:

- [Semantic Versioning](https://semver.org/)
- [Calendar Versioning](https://calver.org/)

Can optionally disable versioning compliance checks.

## Usage Example

<!-- markdownlint-disable MD046 -->

```yaml
steps:
  - name: 'Verify Pushed Tag'
    uses: lfreleng-actions/tag-push-verify-action@main
    with:
      versioning: 'calver'
      exit_on_fail: 'false'
```

<!-- markdownlint-enable MD046 -->

## Tag

The validated tag comes from: `${{ github.ref_name }}`

## Inputs

 <!-- markdownlint-disable MD013 -->

| Input Name   | Required | Default | Description                                                    |
| ------------ | -------- | ------- | -------------------------------------------------------------- |
| versioning   | False    | semver  | Check tag compliance with versioning type [semver/calver/none] |
| exit_on_fail | False    | true    | Exit with error if tag fails versioning compliance check       |

<!-- markdownlint-enable MD013 -->

The action will always exit with an error if a tag push event did not trigger
the action/workflow run. When "exit_on_fail" set false, the versioning
type/compliance check generates a warning rather than an error.

## Versioning Types

The "versioning" input string must match one of the options below:

 <!-- markdownlint-disable MD013 -->

| Versioning | Description                 |
| ---------- | --------------------------- |
| semver     | Semantic versioning         |
| calver     | Calendar versioning         |
| none       | No tag validation performed |

<!-- markdownlint-enable MD013 -->

## Outputs

<!-- markdownlint-disable MD013 -->

| Output Name | Description                                              |
| ----------- | -------------------------------------------------------- |
| valid       | Set based on the validation results: true/false/untested |
| tag         | Set to the pushed tag value ${{ github.ref_name }}       |

Note: also exports the pushed tag to the environment.

<!-- markdownlint-enable MD013 -->
