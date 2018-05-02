channeled-dashboard_deployment
==============================

Sample ansible script to deploy **channeled-dashboard** project
(either channels1 or channels2 branches):

- http://channeled-dashboard-demo1.brainstorm.it/   (channel1 version)
- http://channeled-dashboard-demo2.brainstorm.it/   (channel2 version)

Test with these credentials:

- username: guest1
- password: guest1

- username: guest2
- password: guest2


Usage
=====

Provisioning (run this only once per server)
--------------------------------------------

$ ansible-playbook -v -i hosts provisioning.yml demo1


Deployment (run this for every instance)
----------------------------------------

$ ansible-playbook -v -i hosts deployment.yml demo1


Fix Ubuntu 16.04 LTS doesn't come with certain modules, required by ansible
---------------------------------------------------------------------------

.. code :: bash

    apt-get install python-minimal aptitude -y  (on target)

or (from deployment host):

.. code :: bash

    ssh REMOTE_HOST "sudo apt-get install python-minimal aptitude -y"


Caveats
=======

For some reason, I had to create the virtual env for each instance manually;
after creation, virtualenv update works as expected via ansible deployment procedure.

::

    su demo1
    cd
    python3.6 -m venv python

::

    su demo2
    cd
    python3.6 -m venv python



