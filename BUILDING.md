# Uploading the component

This component does not require any external dependency. To build and upload you can run:

```bash
ggcli init
ggcli component upload -n community.greengrass.routing.tes
```

## Testing


To test you can upload and deploy the `test.docker.tes` component.

1. Build the docker file first and upload the container image to a docker repository (eg ECR).
2. Modify the recipe to refer to the container image
1. Upload and deploy

This component creates a Jupyter notebook running on port `8898` of the host. `boto3` is pre-installed in the container.

You can get token to access the notebook from `/greengrass/v2/logs/test.docker.tes.log` file.

Create a notebook and test with `boto3`.