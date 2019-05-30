## abrir el puerto 8000 sobre la VM master del cluster EMR 

## contectarse al master del EMR-AWS:

    ssh -i ~/st01800.pem hadoop@ec2-18-208-213-45.compute-1.amazonaws.com
    $ sudo su
    # passwd hadoop
    // coloquele el password que desee a hadoop
    # su - hadoop

## instalar node:

ref: https://www.e2enetworks.com/help/knowledge-base/how-to-install-node-js-and-npm-on-centos/

como 'root':

    # yum install -y gcc-c++ make
    # curl -sL https://rpm.nodesource.com/setup_6.x | sudo -E bash -
    # yum install -y nodejs
    # npm install -g configurable-http-proxy


## instalar virtualenv:

ref: https://rukbottoland.com/blog/tutorial-de-python-virtualenv/

    # su - hadoop
    $ virtualenv env --python=python3
    $ cd env
    $ source bin/activate
    (env) ...
    (env)...
    (env) $ deactivate

## instalar jupyterhub:
ref: https://jupyterhub.readthedocs.io/en/stable/quickstart.html

    $ cd env
    $ source bin/activate
    (env)$ python3 -m pip install jupyterhub
    (env)$ npm install configurable-http-proxy
    (env)$ python3 -m pip install notebook

instalar dependencias: 

    (env)$ easy_install jinja2 sqlalchemy tornado notebook 

ejecutar jupyterhub:

    (env)$ jupyterhub --port 8080

abra un browser:

    http://ec2-18-208-213-45.compute-1.amazonaws.com:8000
