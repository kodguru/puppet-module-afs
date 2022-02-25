# Reference

<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

### Classes

* [`afs`](#afs): This module manages OpenAFS

### Defined types

* [`afs::validate_domain_names`](#afsvalidate_domain_names): == Define: afs::validate_domain_names iteration in Puppet 3 style

## Classes

### <a name="afs"></a>`afs`

afs class

#### Examples

##### Declaring the class

```puppet
include ::afs
```

#### Parameters

The following parameters are available in the `afs` class:

* [`afs_cellserverdb`](#afs_cellserverdb)
* [`afs_cell`](#afs_cell)
* [`afs_config_path`](#afs_config_path)
* [`afs_cron_job_content`](#afs_cron_job_content)
* [`afs_cron_job_hour`](#afs_cron_job_hour)
* [`afs_cron_job_interval`](#afs_cron_job_interval)
* [`afs_cron_job_minute`](#afs_cron_job_minute)
* [`afs_cron_job_monthday`](#afs_cron_job_monthday)
* [`afs_cron_job_month`](#afs_cron_job_month)
* [`afs_cron_job_weekday`](#afs_cron_job_weekday)
* [`afs_suidcells`](#afs_suidcells)
* [`cache_path`](#cache_path)
* [`cache_size`](#cache_size)
* [`config_client_args`](#config_client_args)
* [`config_client_clean_cache_on_start`](#config_client_clean_cache_on_start)
* [`config_client_dkms`](#config_client_dkms)
* [`config_client_path`](#config_client_path)
* [`config_client_update`](#config_client_update)
* [`create_symlinks`](#create_symlinks)
* [`init_script`](#init_script)
* [`init_template`](#init_template)
* [`systemd_script_template`](#systemd_script_template)
* [`systemd_unit_template`](#systemd_unit_template)
* [`links`](#links)
* [`package_adminfile`](#package_adminfile)
* [`package_name`](#package_name)
* [`package_provider`](#package_provider)
* [`package_source`](#package_source)
* [`service_provider`](#service_provider)

##### <a name="afs_cellserverdb"></a>`afs_cellserverdb`

Data type: `Optional[String]`

String defining CellServDB. Content of file $afs_config_path/CellServDB.
This file will be ignored if the default value is not changed.

Default value: ``undef``

##### <a name="afs_cell"></a>`afs_cell`

Data type: `Optional[String]`

String defining ThisCell. Content of the file $afs_config_path/ThisCell.
This file will be ignored if the default value is not changed.

Default value: ``undef``

##### <a name="afs_config_path"></a>`afs_config_path`

Data type: `Stdlib::Unixpath`

Path to the OpenAFS config directory.

Default value: ``undef``

##### <a name="afs_cron_job_content"></a>`afs_cron_job_content`

Data type: `Optional[String]`

String with OpenAFS cron job command. Example: '[ -x /afs_maintenance.sh ] && /afs_maintenance.sh'
Do not use multi line content when $afs_cron_job_interval is set to 'specific'.

Default value: ``undef``

##### <a name="afs_cron_job_hour"></a>`afs_cron_job_hour`

Data type: `Optional[Integer[0, 23]]`

The hour at which to run the cron job.
If set to <undef> it will become '*' at creation time.

Default value: ``undef``

##### <a name="afs_cron_job_interval"></a>`afs_cron_job_interval`

Data type: `Optional[Enum['hourly', 'daily', 'weekly', 'monthly', 'specific']]`

String to specify when to run the cron job.
Set to 'specific' to create cron jobs. It uses $afs_cron_job_minute/hour/weekday/month/monthday
to specify when to run the cron job.
On systems that support fragment files in /etc/cron.(hourly|daily|weekly|monthly) you can use
This module can only create or change cron jobs, there is no housekeeping support to delete them.

Default value: ``undef``

##### <a name="afs_cron_job_minute"></a>`afs_cron_job_minute`

Data type: `Optional[Integer[0, 59]]`

Integer within specific boundaries. The minute at which to run the cron job.
ACHTUNG: If set to <undef> it will become '*' at creation time.

Default value: `42`

##### <a name="afs_cron_job_monthday"></a>`afs_cron_job_monthday`

Data type: `Optional[Integer[1, 31]]`

Integer within specific boundaries. The day of the month on which to run the cron job.
If set to <undef> it will become '*' at creation time.

Default value: ``undef``

##### <a name="afs_cron_job_month"></a>`afs_cron_job_month`

Data type: `Optional[Integer[1, 12]]`

Integer within specific boundaries. The month of the year in which to run the cron job.
If set to <undef> it will become '*' at creation time.

Default value: ``undef``

##### <a name="afs_cron_job_weekday"></a>`afs_cron_job_weekday`

Data type: `Optional[Integer[0, 7]]`

Integer within specific boundaries. The weekday on which to run the cron job. 0 and 7 are both for Sundays.
If set to <undef> it will become '*' at creation time.

Default value: ``undef``

##### <a name="afs_suidcells"></a>`afs_suidcells`

Data type: `Variant[Array[String], String]`

Array of strings with content of the file $afs_config_path/SuidCells.
This file will be ignored if the default value is not changed.

Default value: `[]`

##### <a name="cache_path"></a>`cache_path`

Data type: `Stdlib::Unixpath`

Path to cache storage when using disk cache.
Recommended: use a dedicated partition as disk cache.

Default value: ``undef``

##### <a name="cache_size"></a>`cache_size`

Data type: `Integer`

Cache size in kb.
'1000000' = 1GB is a good value for single user systems
'4000000' = 4GB is a good value for terminal servers
ACHTUNG!: real occupied space can be 5% larger, due to metadata

Default value: `1000000`

##### <a name="config_client_args"></a>`config_client_args`

Data type: `String`

AFSD_ARGS / parameters to be passed to AFS daemon while starting.
Since 1.6.x the afs-client has integrated auto-tuning.
Specifying more options for tuning should only be applied after monitoring the system.
Candidates for tuning: -stat, -volumes

Default value: `'-dynroot -afsdb -daemons 6 -volumes 1000'`

##### <a name="config_client_clean_cache_on_start"></a>`config_client_clean_cache_on_start`

Data type: `Boolean`

Boolean trigger for the cleaning of the client cache on start.
If set to true, the provided init script will clean the client cache when starting the service.
Please check openafs-client config file for supported OS families.

Default value: ``false``

##### <a name="config_client_dkms"></a>`config_client_dkms`

Data type: `Boolean`

Boolean to control the AFS kernel module handling via DKMS or the openafs start-script.
At the moment only available on RHEL platform. It will be ignored on other platforms.

Default value: ``undef``

##### <a name="config_client_path"></a>`config_client_path`

Data type: `Stdlib::Unixpath`

Path to the openafs-client configuration file.

Default value: ``undef``

##### <a name="config_client_update"></a>`config_client_update`

Data type: `Boolean`

Boolean trigger for the selfupdating routine in the init script.
If set to true, the init skript checks for updated AFS packages in the available repositories and installs them.

Default value: ``false``

##### <a name="create_symlinks"></a>`create_symlinks`

Data type: `Boolean`

Create symlinks for convenient access to AFS structure. Path and target are taken from hash in $links.

Default value: ``false``

##### <a name="init_script"></a>`init_script`

Data type: `Stdlib::Unixpath`

Filename for the init script.

Default value: `'/etc/init.d/openafs-client'`

##### <a name="init_template"></a>`init_template`

Data type: `Optional[String]`

Name of the template file to be used for $init_script.
Installs init-script if specified.

Default value: ``undef``

##### <a name="systemd_script_template"></a>`systemd_script_template`

Data type: `Optional[String]`

Name of the template file to be used as startup script for systemd.
Installs systemd script if specified.

Default value: ``undef``

##### <a name="systemd_unit_template"></a>`systemd_unit_template`

Data type: `Optional[String]`

Name of the template file to be used as unit file for systemd.
Installs systemd unit file if specified.

Default value: ``undef``

##### <a name="links"></a>`links`

Data type: `Optional[Hash]`

Hash of path and target to create symlinks from if $create_links is true.

Default value: `{}`

##### <a name="package_adminfile"></a>`package_adminfile`

Data type: `Optional[String]`

Solaris specific: string with adminfile.

Default value: ``undef``

##### <a name="package_name"></a>`package_name`

Data type: `Variant[Array[String], String]`

Array or string of needed OpenAFS packages.

Default value: ``undef``

##### <a name="package_provider"></a>`package_provider`

Data type: `Optional[String]`

Solaris specific: string with package source.

Default value: ``undef``

##### <a name="package_source"></a>`package_source`

Data type: `Optional[String]`

Solaris specific: string with package source.

Default value: ``undef``

##### <a name="service_provider"></a>`service_provider`

Data type: `Optional[String]`

String of which service provider should be used

Default value: ``undef``

## Defined types

### <a name="afsvalidate_domain_names"></a>`afs::validate_domain_names`

== Define: afs::validate_domain_names
iteration in Puppet 3 style
