We have multiple AWS builder types to create image. we can choose one depending on what kind of image we need.

The most simple, [easiest and widely used AWS builder](https://www.packer.io/docs/builders/amazon-ebs.html) is `amazon-ebs`. 

When using this builder, there are some `required` attributes we should be passing.

Required Configuration:
----------------------
1. Access Configuration
    ```
     access_key
     secret_key
     region
    ```

2. AMI Configuration. 
    `ami-name`

3. Run Configuration
   ```
   instance_type
   source_ami
   
   ```