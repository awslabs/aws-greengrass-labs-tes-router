# Test the aws.greengrass.labs.router.tes component

The `aws.greengrass.labs.router.tes` component is used to allow containers not running with host networking to access the credential endpoint provided by the Greengrass TES component.

This sample component deploys a Jupyter notebook running in a container on your target device using the default bridge networking. 

As you can see in the recipe, we are forcing the `AWS_CONTAINER_CREDENTIALS_FULL_URI` to assume the value of the standard ECS credential endpoint 

```yaml
-e AWS_CONTAINER_CREDENTIALS_FULL_URI='http://169.254.170.2/2016-11-01/credentialprovider/
```

Once deployed you'll have a Jupyter notebook accessible on port 8898 on your device. If you are using EC2 as your test device, you can forward the remote port to your machine using SSH and then access the notebook by opening the notebook URL from your machine.

On your computer:
```
ssh -L 8898:localhost:8898 -i <key> ubuntu@1.2.3.4
```

In the ssh session:
```
sudo cat /greengrass/v2/logs/test.docker.tes.log
```

The latter command will print the logs of the component containing the Jupyter notebook URL that you need to copy to your browser. It should look something like: 

```
http://127.0.0.1:8888/lab?token=bccbe0361cd9854ab8f1f9a3298e16c966b2f94b8cab3620
```

Once you have Jupyter running in the browser, you can execute the following lines in a cell:

```python
%pip install boto3
import boto3
c = boto3.client('sts')
c.get_caller_identity()
``` 



