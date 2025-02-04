---
title: atmos aws eks update-kubeconfig
sidebar_label: eks update-kubeconfig
sidebar_class_name: command
id: eks-update-kubeconfig
description: Use this command to download `kubeconfig` from an EKS cluster and saves it to a file.
---

:::info Purpose
Use this command to download `kubeconfig` from an EKS cluster and save it to a file.
:::

Executes `aws eks update-kubeconfig` command.

```shell
atmos aws eks update-kubeconfig [options]
```

This command executes `aws eks update-kubeconfig` command to download `kubeconfig` from an EKS cluster and saves it to a file.

The command can execute `aws eks update-kubeconfig` in three different ways:

1. If all the required parameters (cluster name and AWS profile/role) are provided on the command-line, then `atmos` executes the command without
   requiring the `atmos` CLI config and context.

  For example:

  ```shell
  atmos aws eks update-kubeconfig --profile=<profile> --name=<cluster_name>
  ```

1. If `component` and `stack` are provided on the command-line, then `atmos` executes the command using the `atmos` CLI config and stack's context by
   searching for the following settings:

   - `components.helmfile.cluster_name_pattern` in the `atmos.yaml` CLI config (and calculates the `--name` parameter using the pattern)
   - `components.helmfile.helm_aws_profile_pattern` in the `atmos.yaml` CLI config (and calculates the `--profile` parameter using the pattern)
   - `components.helmfile.kubeconfig_path` in the `atmos.yaml` CLI config the variables for the component in the provided stack
   - `region` from the variables for the component in the stack

  For example:

  ```shell
  atmos aws eks update-kubeconfig <component> -s <stack>
  ```

1. Combination of the above. Provide a component and a stack, and override other parameters on the command line.

  For example:

  ```shell
  atmos aws eks update-kubeconfig <component> -s <stack> --kubeconfig=<path_to_kubeconfig> --region=us-east-1
  ```

<br/>

:::info
Refer to [Update kubeconfig](https://docs.aws.amazon.com/cli/latest/reference/eks/update-kubeconfig.html) for more information
:::

:::tip
Run `atmos aws eks update-kubeconfig --help` to see all the available options
:::

## Examples

```shell
atmos aws eks update-kubeconfig <component> -s <stack>
atmos aws eks update-kubeconfig --profile=<profile> --name=<cluster_name>
atmos aws eks update-kubeconfig <component> -s <stack> --kubeconfig=<path_to_kubeconfig> --region=<region>
atmos aws eks update-kubeconfig --role-arn <ARN>
atmos aws eks update-kubeconfig --alias <cluster context name alias>
atmos aws eks update-kubeconfig --dry-run=true
atmos aws eks update-kubeconfig --verbose=true
```

## Arguments

| Argument     | Description        | Required |
|:-------------|:-------------------|:---------|
| `component`  | `atmos` component  | no       |

## Flags

| Flag           | Description                                                                                 | Alias | Required |
|:---------------|:--------------------------------------------------------------------------------------------|:------|:---------|
| `--stack`      | `atmos` stack                                                                               | `-s`  | no       |
| `--profile`    | AWS profile to use to authenticate to the EKS cluster                                       |       | no       |
| `--role-arn`   | AWS IAM role ARN to use to authenticate to the EKS cluster                                  |       | no       |
| `--name`       | EKS cluster name                                                                            |       | no       |
| `--region`     | AWS region                                                                                  |       | no       |
| `--kubeconfig` | `kubeconfig` filename to append with the configuration                                      |       | no       |
| `--alias`      | Alias for the cluster context name. Defaults to match cluster ARN                           |       | no       |
| `--dry-run`    | Print the merged kubeconfig to stdout instead of writing it to the specified file           |       | no       |
| `--verbose`    | Print more detailed output when writing the kubeconfig file, including the appended entries |       | no       |
