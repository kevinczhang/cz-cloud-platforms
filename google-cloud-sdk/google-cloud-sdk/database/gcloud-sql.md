---
description: >-
  The gcloud sql command group lets you create and manage Google Cloud SQL
  databases.
---

# gcloud sql

 Cloud SQL is a fully-managed database service that makes it easy to set up, maintain, manage, and administer your relational MySQL databases in the cloud.

 `gcloud sql` [`GROUP`](https://cloud.google.com/sdk/gcloud/reference/sql/#GROUP) \| [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/sql/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/sql/#GCLOUD-WIDE-FLAGS) `…`\]

 `GROUP` is one of the following:

* [`backups`](https://cloud.google.com/sdk/gcloud/reference/sql/backups)Provide commands for working with backups of Cloud SQL instances.
* [`databases`](https://cloud.google.com/sdk/gcloud/reference/sql/databases)Provide commands for managing databases of Cloud SQL instances.
* [`export`](https://cloud.google.com/sdk/gcloud/reference/sql/export)Provide commands to export Cloud SQL instances.
* [`flags`](https://cloud.google.com/sdk/gcloud/reference/sql/flags)Provide a command to list flags.
* [`import`](https://cloud.google.com/sdk/gcloud/reference/sql/import)Provides commands to import Cloud SQL instances.
* [`instances`](https://cloud.google.com/sdk/gcloud/reference/sql/instances)Provide commands for managing Cloud SQL instances.
* [`operations`](https://cloud.google.com/sdk/gcloud/reference/sql/operations)Provide commands for working with Cloud SQL instance operations.
* [`ssl`](https://cloud.google.com/sdk/gcloud/reference/sql/ssl)Provide commands for managing SSL certificates of Cloud SQL instances.
* [`ssl-certs`](https://cloud.google.com/sdk/gcloud/reference/sql/ssl-certs)`(DEPRECATED)` Provide commands for managing SSL certificates of Cloud SQL instances.
* [`tiers`](https://cloud.google.com/sdk/gcloud/reference/sql/tiers)Provide a command to list tiers.
* [`users`](https://cloud.google.com/sdk/gcloud/reference/sql/users)Provide commands for managing Cloud SQL users.

`COMMAND` is one of the following:[`connect`](https://cloud.google.com/sdk/gcloud/reference/sql/connect)Connects to a Cloud SQL instance.

## gcloud sql instances create - creates a new Cloud SQL instance

 `gcloud sql instances create` [`INSTANCE`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#INSTANCE) \[[`--activation-policy`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--activation-policy)=`ACTIVATION_POLICY`\] \[[`--assign-ip`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--assign-ip)\]\[[`--async`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--async)\] \[[`--authorized-gae-apps`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--authorized-gae-apps)=`APP`,\[[`APP`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#APP),…\]\] \[[`--authorized-networks`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--authorized-networks)=`NETWORK`,\[[`NETWORK`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#NETWORK),…\]\]\[[`--availability-type`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--availability-type)=`AVAILABILITY_TYPE`\] \[[`--no-backup`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--backup)\]\[[`--backup-start-time`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--backup-start-time)=`BACKUP_START_TIME`\] \[[`--cpu`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--cpu)=`CPU`\]\[[`--database-flags`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--database-flags)=`FLAG`=`VALUE`,\[[`FLAG`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#FLAG)=`VALUE`,…\]\] \[[`--database-version`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--database-version)=`DATABASE_VERSION`\]\[[`--enable-bin-log`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--enable-bin-log)\] \[[`--failover-replica-name`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--failover-replica-name)=`FAILOVER_REPLICA_NAME`\]\[[`--follow-gae-app`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--follow-gae-app)=`FOLLOW_GAE_APP`\]\[[`--maintenance-release-channel`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--maintenance-release-channel)=`MAINTENANCE_RELEASE_CHANNEL`\]\[[`--maintenance-window-day`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--maintenance-window-day)=`MAINTENANCE_WINDOW_DAY`\]\[[`--maintenance-window-hour`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--maintenance-window-hour)=`MAINTENANCE_WINDOW_HOUR`\]\[[`--master-instance-name`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--master-instance-name)=`MASTER_INSTANCE_NAME`\] \[[`--memory`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--memory)=`MEMORY`\]\[[`--pricing-plan`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--pricing-plan)=`PRICING_PLAN`, [`-p`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#-p) [`PRICING_PLAN`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#PRICING_PLAN); default="PER\_USE"\]\[[`--replica-type`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--replica-type)=`REPLICA_TYPE`\] \[[`--replication`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--replication)=`REPLICATION`\] \[[`--require-ssl`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--require-ssl)\]\[[`--root-password`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--root-password)=`ROOT_PASSWORD`\] \[[`--storage-auto-increase`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--storage-auto-increase)\] \[[`--storage-size`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--storage-size)=`STORAGE_SIZE`\]\[[`--storage-type`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--storage-type)=`STORAGE_TYPE`\] \[[`--tier`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--tier)=`TIER`, [`-t`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#-t) [`TIER`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#TIER)\] \[[`--region`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--region)=`REGION`; default="us-central"    \| [`--gce-zone`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--gce-zone)=`GCE_ZONE`     \| [`--zone`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#--zone)=`ZONE`\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/sql/instances/create#GCLOUD-WIDE-FLAGS) `…`\]

## gcloud sql databases create - creates a database for a Cloud SQL instance

 `gcloud sql databases create` [`DATABASE`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#DATABASE) [`--instance`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#--instance)=`INSTANCE`, [`-i`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#-i) [`INSTANCE`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#INSTANCE) \[[`--async`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#--async)\]\[[`--charset`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#--charset)=`CHARSET`\] \[[`--collation`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#--collation)=`COLLATION`\] \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/sql/databases/create#GCLOUD-WIDE-FLAGS) `…`\]

## gcloud sql backups

Provide commands for working with backups of Cloud SQL instances including listing and getting information about backups for a Cloud SQL instance.

 `gcloud sql backups` [`COMMAND`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/#COMMAND) \[[`GCLOUD_WIDE_FLAG`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/#GCLOUD-WIDE-FLAGS) `…`\]

 `COMMAND` is one of the following:

* [`create`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/create)Creates a backup of a Cloud SQL instance.
* [`delete`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/delete)Delete a backup of a Cloud SQL instance.
* [`describe`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/describe)Retrieves information about a backup.
* [`list`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/list)Lists all backups associated with a given instance.
* [`restore`](https://cloud.google.com/sdk/gcloud/reference/sql/backups/restore)Restores a backup of a Cloud SQL instance.

