# Node.js application provisioner to ec2

This sample project will help you provision Node.js application to ec2 instance with [Ansible](https://docs.ansible.com/ansible/index.html).


## Prerequisites
You need to have pip and ansible [installed](http://docs.ansible.com/ansible/intro_installation.html#latest-releases-via-pip).

## Deploy

 0. Clone project:

    ```shell
    git clone https://github.com/shirkevich/ansible-ec2-nodejs.git
    ```

 1. Install required python libraries:

    ```shell
    pip install -r requirements.txt
    ```
 2. Install ansible roles

    ```shell
    ansible-galaxy install -r requirements.yml
    ```

 2. Export aws access_key, secret and region:

    ```shell
    export AWS_ACCESS_KEY_ID=xxxx
    export AWS_SECRET_ACCESS_KEY=yyyy
    export EC2_REGION=us-east-1
    ```

 3. Edit [example.yml](example.yml) and set following variables:

  * app_git_url
  * nginx_application_path

 4. Run provision with:

    ```shell
    ansible-playbook example.yml
    ```

## Cleanup

 1. update inventory cache for ec2

    ```shell
    ./inventory/ec2.py --refresh-cache
    ```

 2. stop started instance with

    ```shell
    ansible-playbook cleanup.yml
    ```
