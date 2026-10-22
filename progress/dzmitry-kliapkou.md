2026-03-27 Fri:

This week main focus was onboarding into the project, understanding existing infrastructure, workflows and operational practices. I spent time reviewing current Ansible setup, monitoring stack, alerting rules and deployment processes to build a complete picture of the system.

From the infrastructure side, I reworked the inventory structure. Previously, the project was using monolithic TOML inventory files where hosts, groups and variables were mixed together. I migrated this to a YAML-based inventory with proper separation into group_vars and host_vars. This significantly improves maintainability and reduces risk of configuration errors.

During this migration, I encountered an issue with boolean values being rendered incorrectly in the Harmony TOML configuration (uppercase True/False coming from YAML). I updated the template to safely normalize boolean values to lowercase, ensuring compatibility with the application config format.

Additionally, I improved monitoring configuration:

- Improved generation of Prometheus scrape configs via Ansible templates
- Added alert for missing log ingestion (promtail not sending logs)
- Excluded archival nodes from disk usage percentage alerts, since their large disks made percentage-based alerts noisy and not actionable

From the deployment side, I extended existing functionality for using local Harmony binaries. Previously this was supported only in the upgrade playbook; I added the same capability to the install playbook, enabling more flexible testing of development builds.

Operationally, I handled routine on-call activities:
- Responded to Grafana alerts and investigated triggered issues
- Performed Harmony app updates on several devnet hosts upon developer request
- Continued familiarization with system behavior under real incidents

Overall, the week was focused on improving infrastructure clarity, fixing configuration edge cases, and establishing a more maintainable foundation for further work.
