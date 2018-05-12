# terraform-provider-circleci

[Terraform][] provider for [CircleCI][].

## Provider

The CircleCI provider is used to interact with CircleCI resources.

The provider allows you to manage your CircleCI projects and their environment
variables easily. It needs to be configured with the proper credentials before
it can be used.

#### Example Usage

```hcl
provider "circleci" {
  token        = "${var.circleci_token}"
  organization = "${var.circleci_organization}"
}
```

#### Argument Reference

The following arguments are supported in the `provider` block:

* `token` - (Optional) This is the CircleCI API token. It must be provided,
  but it can also be sourced from the `CIRCLECI_TOKEN` environment variable.

* `organization` - (Optional) This is the organization/account to be managed.
  It must be provided, but it can also be sourced from the `CIRCLECI_ORGANIZATION`
  environment variable.

---

## Data Sources

@TODO

---

## Resources

### circleci_project

Provides a CircleCI project resource.

This resource allows you to start/stop building projects from your organization.
When applied, a project is enabled. When destroyed, that project will be disabled.

#### Example Usage

```hcl
resource "circleci_project" "myproj" {
  name = "myproj"

  env_vars {
    SOME_TOKEN = "a1b2c3d4e5f6g7h8i9j0"
  }
}
```

#### Argument Reference

The following arguments are supported:

* `name` - (Required) The name of the project/repository.

* `env_vars` - (Optional) A mapping of environment variables to assign to the
  resource.

#### Import

CircleCI projects can be imported using the name, e.g.

```shell
$ terraform import circleci_project.myproj myproj
```

## License

terraform-provider-circleci is released under the [Mozilla Public License 2.0][].

[Terraform]: https://www.terraform.io
[CircleCI]: https://circleci.com
[Mozilla Public License 2.0]: https://github.com/thiagoalessio/terraform-provider-circleci/blob/master/LICENSE
