---
title: atmos describe config
sidebar_label: config
sidebar_class_name: command
id: config
description: Use this command to show the final (deep-merged) CLI configuration of all `atmos.yaml` file(s).
---

:::note Purpose
Use this command to show the final (deep-merged) CLI configuration of all `atmos.yaml` file(s).
:::

## Usage 

Execute the `describe config` command like this:

```shell
atmos describe config [options]
```

This command shows the final (deep-merged) CLI configuration (from `atmos.yaml` file(s)).

:::tip
Run `atmos describe config --help` to see all the available options
:::

## Examples

```shell
atmos describe config
atmos describe config -f yaml
atmos describe config --format yaml
atmos describe config -f json
```

## Flags

| Flag        | Description                                         | Alias | Required |
|:------------|:----------------------------------------------------|:------|:---------|
| `--format`  | Output format: `json` or `yaml` (`json` is default) | `-f`  | no       |
