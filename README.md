Small reproduction for https://github.com/coder/coder/issues/3938 using Coder CLI tool v0.9.3.

Assuming you've already run `coder login ...` to login to a Coder server, clone this repo and `cd` to its root folder and then run:

```
❯ git submodule update --init --recursive
```

```
❯ terraform init
Initializing modules...

Initializing the backend...

Initializing provider plugins...
- Reusing previous version of coder/coder from the dependency lock file
- Reusing previous version of hashicorp/aws from the dependency lock file
- Using previously-installed coder/coder v0.5.0
- Using previously-installed hashicorp/aws v4.33.0

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

```
❯ pushd terraform-aws-ec2-instance
```

```
❯ terraform init

Initializing the backend...

Initializing provider plugins...
- Reusing previous version of hashicorp/aws from the dependency lock file
- Using previously-installed hashicorp/aws v4.33.0

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

```
❯ popd
```

```
❯ coder templates create test-publish
> Create and upload "~/Development/repro-coder-template-push-failure"? (yes/no)
Archive too big. Must be <= 1048576 bytes
Run 'coder templates create --help' for usage.
```

Here are the versions of the tools I'm using:

```
❯ coder version
Coder v0.9.3+504cd46 Wed Oct  5 00:46:59 UTC 2022
https://github.com/coder/coder/commit/504cd462a738187fa4c4d8d80d9828b23ed50e8c


❯ terraform --version
Terraform v1.3.1
on darwin_amd64
```
