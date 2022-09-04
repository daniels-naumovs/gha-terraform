# Terraform Github Action

This Action runs most Terraform commands commonly used in CI so you can interact
with your Terraform-based infrastructure. It does this by being given a target
(last) step to run and then it runs it, along with every prerequisite command.
For example, if the last step is `plan`, the action will also run `fmt`, `init`,
etc. See [Usage](#usage) for a tree of what steps can and are run.

Common use cases for this Action would be to automatically provision Terraform
resources via `apply` in CI/CD pipelines or to manually run semi-frequently used
commands, such as `import`.

# Usage

```yml
jobs:
  <job_id>:
    steps:

    # Clone the repository to use the Action. Necessary because the Actions' code is
    # in a private repository.
    - name: Checkout Terraform Action repository
      uses: actions/checkout@v3
      with:
        path: .github/actions/gha-terraform-ci
        ref: v2.1.0
        repository: workivate/gha-terraform-ci

        # This GitHub personal access token should have at least read access to the
        # repository this Action is in in order to pull it.
        token: ${{ secrets['<git_token>'] }}

    - name: Run Terraform Action

      # Make sure this path matches whatever you've set 'path' to in the checkout step
      # above and is preceded by './' as in this example.
      uses: ./.github/actions/gha-terraform-ci

      with:

        # The Terraform resource address to import.
        #
        # Only used when 'step' is set to 'import'.
        import_address: ''

        # The provider-based target resource.
        #
        # Only used when 'step' is set to 'import'.
        import_id: ''

        # The ID of the backend-dependant state lock to unlock.
        #
        # Only used when 'step' is set to 'force-unlock'.
        lock_id: ''

        # The last Terraform command to run in the sequence.
        #
        # The command sequence is as follows:
        # fmt
        # └── init
        #     └── validate
        #         ├── plan
        #         │   └── apply
        #         ├── destroy
        #         ├── import
        #         └── force-unlock
        #
        # Available options: fmt, validate, plan, apply, destroy, import, force-unlock
        #
        # 'init' is not in the list of options since there is no functional purpose to
        # run it as the last command. It always runs whenever it is required as a
        # prerequisite for another command, such as 'plan'.
        step: apply

        # The version of Terraform to use when running this Action.
        #
        # Default: 1.1.9
        terraform_version: 1.0.0

        # Here you can specify flags for each Terraform command that will run in the
        # sequence you choose. Replace <step> with the name of one of the steps that you
        # wish to customize.
        #
        # Remember to specify multiple variables, each corresponding to a step that
        # needs custom flags.
        #
        # Defaults:
        # * apply: 'tfplan'
        # * force-unlock: '--force'
        # * fmt: '--check --diff'
        # * plan: '--out=tfplan'
        # * destroy: '--auto-approve'
        # * init, validate, import: ''
        TF_CLI_ARGS_<step>: ''

        # The directory to execute Terraform commands from.
        #
        # Default: '${{ github.workspace }}/terraform'
        working-directory: ''
```

# Scenarios

All of the scenarios assume that you cloned this repository via
`actions/checkout@v3` in a previous step, as described in [Usage](#usage).

## Apply configuration

```yml
- name: Apply Terraform Config
  uses: ./.github/actions/gha-terraform-ci
  with:
    step: apply
    TF_CLI_ARGS_init: '--backend-config="bucket=moonbucket" --backend-config="key=moon/terraform.tfstate" --backend-config="region=moon"'
    TF_CLI_ARGS_plan: '--out=tfplan --var-file=moon.tfvars'
    working-directory: 'custom/directory'
```

## Import a resource

```yml
- name: Import Resource Into Terraform
  uses: ./.github/actions/gha-terraform-ci
  with:
  step: import
    TF_CLI_ARGS_init: '--backend-config="bucket=moonbucket" --backend-config="key=moon/terraform.tfstate" --backend-config="region=moon"'
    TF_CLI_ARGS_import: '-var-file=moon.tfvars -var "in_space=true"'
    import_address: 'aws_vpc.moon_vpc'
    import_id: 'vpc-abcd1234'
    terraform_version: '1.2.3'
```
