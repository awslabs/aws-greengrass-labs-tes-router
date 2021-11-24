# community.greengrass.routing.tes

This component configures `nftables` or `iptables` on a Greengrass device to be able to use `aws.greengrass.TokenExchangeService` with containers. The TES port is extracted from the `AWS_CONTAINER_CREDENTIALS_FULL_URI` environment variable and used to create the `nftables/iptables` entries.

If `nftables` exists on the device it will be used, otherwise the component falls back to `iptables`.

If you are creating a component that uses container images as runtime, use this component as dependency and then add the following flags to the command used to run the container (example for `docker`):

```
-e SVCUID \
-e AWS_REGION \
-e AWS_CONTAINER_AUTHORIZATION_TOKEN \ 
-e AWS_CONTAINER_CREDENTIALS_FULL_URI='http://169.254.170.2/2016-11-01/credentialprovider/'
```

For more information on how what this components does, you can check [Enabling Task IAM Roles on your Container Instances](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html#enable_task_iam_roles).


## Versions
This component has the following versions:

* 1.0.x

## Type

This component is a generic component. The [Greengrass nucleus](https://docs.aws.amazon.com/greengrass/v2/developerguide/greengrass-nucleus-component.html) runs the component's lifecycle scripts.

For more information, see [component types](https://docs.aws.amazon.com/greengrass/v2/developerguide/manage-components.html#component-types)


## Requirements

This component requires `iptables` command to be present on the device. 

## Dependencies

When you deploy a component, AWS IoT Greengrass also deploys compatible versions of its dependencies. This means that you must meet the requirements for the component and all of its dependencies to successfully deploy the component. This section lists the dependencies for the released versions of this component and the semantic version constraints that define the component versions for each dependency. You can also view the dependencies for each version of the component in the [AWS IoT Greengrass console](https://console.aws.amazon.com/greengrass). On the component details page, look for the Dependencies list.

### 1.0.0

| Dependency | Compatible versions | Dependency type |
|---|---|---|
| Token exchange service | >=0.0.0 | Hard |

## Configuration

This component does not provide any configuration

## Changelog

The following table describes the changes in each version of the component.

| Version | Changes |
|---|---|
| 1.0.0 | Initial version |
