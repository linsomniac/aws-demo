Creating An Instance
--------------------

Your environment needs to have the AWS keys set via:


  - AWS_ACCESS_KEY
  - AWS_SECRET_KEY

Then you need the AWS configurations in a "~/.aws-test-vars.yml" file
similar to:

    ---
    aws_region: <AWS Region for new instance>
    aws_zone: <AWS Zone for new instance>
    aws_subnet_id: <Subnet to create instance in>
    aws_securitygroup_id: <Security group to include ID>
    aws_login_key_name: <AWS instance key name>

Once done, the instance can be created with:

    ansible-playbook create_instance.yml

This will ask for a name for the instance, which will be set as the hostname.

Running Ansible Site
--------------------

After the create, the "site.yml" playbook is run.  The site playbook can be
run after that by setting up an inventory file such as "hosts", similar to:

    [aws-test]
    10.211.150.132 remote_user=sean become=true

The first line is literal, the second line includes the IP address or host
name of the instance, "remote_user" is the username you can ssh to that host
as, and "become=true" means to use sudo after logging in.
