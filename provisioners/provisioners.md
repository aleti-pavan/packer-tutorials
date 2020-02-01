# Packer provisioners

Where builders actually build the image, provisioners play vital role in terms of what's packaged with in created image. Few examples are 

1. Installing a package/applications

2. Patching Kernel

3. Copying files from source to Image.

4. Creating users     etc. These just few examples and not limited.


While [here's the list of available provisioners](https://packer.io/docs/provisioners/index.html) packer has, you can write your own [custom provisioners](https://packer.io/docs/extending/custom-provisioners.html)

we'll be dealing with few examples of `shell(both inline and script), file and ansible` provisers


## Shell Provisioner

We can use shell provisioner to execute either inline commands or scripts. 

below snippet is to run some inline commands on the image. 

```
"provisioners": [
    {
        "type": "shell",
        "inline": [
            "sudo apt-get update",
            "echo here",
            "sudo apt-get install -y python3"
        ]
    }
]
```

## File provisioner

To copy a file from `source (packer executing machine)` to `image` we use `file` provisioner


### Example 1:

Below snippet is to copy the script and run it.

```

 "provisioners": [
     {
        "type": "file",
        "source": "scripts/myscript.sh",
        "destination": "/tmp/myscript.sh"
     },
     {
        "type": "shell",
        "script": "/tmp/myscript.sh"
    }
 ]

```
The `file` provisioner uploads files to machines built by Packer. The recommended usage of the f`ile provisioner` is to use it to upload files, and then use shell provisioner to move them to the proper place, set permissions, etc. The file provisioner can refer to a single file, such as `index.html`, or an entire directory, such as `directory/`.

### Example 2:

Copy the new `index.html` file

```
"provisioners": [
   {
      "type": "file",
      "source": "index.html",
      "destination": "/usr/share/nginx/html/"
   },   {
      "type": "file",
      "source": "directory-name/",
      "destination": "/usr/share/nginx/html/directory-name/"
   }
]

```

## Ansible Provisioner



```
"provisioners": [
    {
    "type": "shell",
    "script": "provisioners/ansible/ansible.sh"
    },
      {
    "type": "ansible-local",
    "playbook_file": "provisioners/ansible/apache-playbook.yml"
    }
]

```