bvansomeren.backup-server
=========================

A good way to do Rsync backups is to have a backup server pull the backups from the target server
This role and the `bvansomeren.backup` role are complimentary.
Using this role you setup the account on the server side, generate a key for this account and add a cronjob to download a specified folder over rsync on an hourly basis.

Future enhancements: Make this work on FreeBSD, use jails, zfs snapshots. etc

Requirements
------------

You need to also run the `bvansomeren.backup` role on the target server to ensure the backup account is created on the target machine

Role Variables
--------------

Some defaults have been setup for CentOS. You can override these if you want

	backup_rsync_binary: "/usr/bin/rsync"

This is where the rsync binary lives

	backup_home: "home"

The location of the home folders for the backup accounts; Defaults to standard home

The main datastructure for this role works as follows:

	backup_accounts:
	  - test.example.com
	      username: "test_example"
	      target_folder: "~/stuff/"
	      customer: "customer1"
	  - test2.example.com
	      username: "test2_example"
	      target_folder: "~/stuff/"
	      customer: "customer1"


Dependencies
------------

No direct dependency, but it's a good idea to have the target side setup with `bvansomeren.backup`

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
