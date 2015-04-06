# Case Study: Fully HA Webapp Infrastructure
We are going to combine ELB, EC2, and RDS to form webapp infrastructure that has no single point of failure (SPOF). All components must be highly available such as ELB, EC2, and RDS. The final result will be as follow ![Architecure](./fully-ha-webapp.png)

# Implementation Plan
We are going to reuse EC2, RDS, and ELB that have been created before. Make sure they are launched properly. Follow [launch EC2 instance](/launch_ec2_instance/README.html#launching-an-ec2-instance), [launch RDS instance](/launch_rds_instance/README.html#launching-an-rds-instance), and [launch ELB instance](//launch_elb_instance/README.html#launching-an-elb-instance) to launch EC2, RDS, and ELB respectively.

We are going to use laravel 5 sample application to test this infrastructure. To make deployment easier, we are using prebuild docker image at [https://registry.hub.docker.com/u/gdplabs/workshop-sample-laravel5/](https://registry.hub.docker.com/u/gdplabs/workshop-sample-laravel5/).

Here is what need to do:
1. Make new database and user at the RDS MySQL.
2. Install docker at the EC2 instance by following executing `wget -qO- https://get.docker.com/ | sh`
3. Stop nginx at the EC2 instance, `sudo service nginx stop`
4. Run docker containers on the EC2 instance, `sudo docker run --name workshop -d -e DB_HOST=127.0.0.1 -e DB_DATABASE=homestead -e DB_USERNAME=homestead -e DB_PASSWORD=secret -p 80:8000 gdplabs/workshop-sample-laravel5`. Don't forget to adjust value of database host, name, username, and password.
5. Launch a second EC2 instance.
6. Run step #2 and #4 at the second EC2 instance.
7. Register the second EC2 instance to the ELB.
8. Modify health check of the ELB from */index.html* to */*.
9. Wait until status of ELB instances is *InService*.
10. Access the app by using ELB Domain Name.
