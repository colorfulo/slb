# Overdue instructions {#concept_lb1_w3n_22b .concept}

The load balancing service will not be stopped immediately if an SLB bill is overdue. Renew Server Load Balancer in time to avoid service interruption.

The following will happen when a Pay-As-You-Go instance is overdue:

-   After a bill is overdue, the instance will keep running for 15 days. Then, the instance will be locked and stop service.

    Once the instance stop running, billing is also stopped.

-   If the SLB bill is still overdue after 15 days the instance is locked, the instance will be automatically released.

    The account owner will receive an email notification one day before the instance is released. The instance configuration and related data will be deleted and cannot be restored after the instance is released.


