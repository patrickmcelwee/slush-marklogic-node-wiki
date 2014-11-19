# Requirements

Slush depends on Node.js to run. You can install it using the Node package manager NPM. It also relies on Gulp to execute its tasks. A convenient way to install Node.js and NPM using RPM and Yum is:

    $ rpm --import https://fedoraproject.org/static/0608B895.txt
    $ rpm -Uvh http://download-i2.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm
    $ yum -y install nodejs npm --enablerepo=epel

After that you can install Gulp and Slush with:

    $ npm install -g gulp
    $ npm install -g slush

You will also need to install this Slush template:

    $ npm install -g slush-marklogic-node

This Slush template uses Roxy to do part of its work. That depends on Git, which can be installed with Yum using:

    $ yum -y install git

This Slush template also makes use of Bower. It can be useful to install that globally using:

    $ npm install -g bower

You will need to take these steps only once, and only for those tools that aren't available yet.

# Generating a project

Go to the directory where your new project should be created. The generator will create a sub-folder with the name of your application. You only need to run this command:

    $ slush marklogic-node <app-name>

It results in an entire project folder. The structure is described in [[Project folder structure]]. To get up and running, you need to take a few additional steps. These are described in [[Deployment process]]. In addition you might want to take a look at the base application. The [README](https://github.com/marklogic/slush-marklogic-node/blob/master/README.mdown) describes how you can load some sample data.