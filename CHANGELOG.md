# managed-automate2 CHANGELOG

This file is used to list changes made in each version of the managed-automate2 cookbook.

# 0.1.0

- Initial release.
- airgap_bundle downloads aib file
- default recipe installs automate

# 0.2.0

- default recipe configures to pass preflight check

# 0.3.0

- default recipe applies license

# 0.4.0

- relax Chef version to 13 from 14, adding sysctl cookbook

# 0.5.0

- aib as a URL or a file in the default recipe
- license as a URL or a string in the default recipe

# 0.6.0

- Original AIB filename is now preserved in addition to generic name.
- Add support for backup recipe and restoring from a backup file.

# 0.7.0

- refactored install/restore/upgrade logic to manage upgrades

# 0.7.1

- code cleanup and updated tests

# 0.8.0

- added Elasticsearch tuning via the private `_elasticsearch.rb` recipe

# 0.9.0

- move to Chef 14/15 and add testing support
- remove sysctl cookbook dependency

# 0.10.0

- change cookbook name from 'managed-automate2' to 'managed_automate'
  - refactor attributes from 'ma2' to 'ma' namespace
- refactor to Custom Resources
- fix broken backups and restore
- much more testing of upgrades
- more resilient to nils
- [https://github.com/mattray/managed-automate2-cookbook/issues/9](airgap_bundle safe for multiple runs)

# 0.10.1

- catch failures on defined paths with no files

# 0.10.2

- changed automate_backup resource with following
  - used backup_directory variable instead of fcp for creating backup script and cron
  - fixed file resource issue

# 0.11.0

- refactor default recipe into separate install, upgrade, and restore recipes
- move upgrade action from automate_airgap_install into new automate_airgap_upgrade custom resource
- fix broken backup and restore resources
- API tests to ensure working restores

# 0.11.1

- [https://github.com/mattray/managed_automate-cookbook/issues/18](include the automate-credentials.toml in the backups)

# 0.11.2

- Cookstyle automated cleanups

# 0.11.3

- [https://github.com/mattray/managed-automate2-cookbook/issues/8](wait for completion of upgrade before proceeding)

# BACKLOG
- replace attributes with inputs for InSpec 4 tests (ChefDK 4)
- download Automate by version
here are all the versions: https://packages.chef.io/manifests/current/automate/versions.json
And you can get a specific version's manifest by replacing latest in the first link with the build number
e.g. https://packages.chef.io/manifests/current/automate/20191015190829.json
Process for creating a bundle:
• download that file to manifest.json
• run chef-automate airgap bundle create -m manifest.json
• that outputs a file and prints the instructions
