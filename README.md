# Automated IAM JML & Access Reconciliation Dashboard

An Identity and Access Management (IAM) lifecycle automation and access reconciliation project built with **Python**, **Flask**, **HTML/CSS**, and **MySQL**.

## Project Structure
- `jml_engine.py`: Automates Joiner provisioning, Mover role/group updates, and Leaver access revocation using RBAC mapping (`ROLE_TO_GROUP`).
- `reconcile_iam.py`: Detects group drift, inactive/stale access, and orphan accounts missing from HR, with `--fix` auto-remediation support.
- `server.py`: Flask backend serving the web UI and REST API endpoints (`/api/state`, `/api/run-jml`, `/api/run-reconcile`, `/api/joiner`, `/api/mover`, `/api/leaver`, `/api/orphan`).
- `templates/index.html`: Custom HTML/CSS interface to trigger JML sync and reconciliation runs, simulate HR/access changes, and view live MySQL tables.

## MySQL Database (`iam_project`)
- `employees`: Authoritative HR source (`emp_id`, `full_name`, `email`, `job_title`, `status`)
- `target_accounts`: Target system access state (`emp_id`, `username`, `assigned_group`, `account_status`)
- `audit_logs`: Audit trail of provisioning, mover updates, leaver revocations, and reconciliation findings

## How to Run Locally
1. Ensure MySQL is running with the `iam_project` database and required tables.
2. Install dependencies:
   ```powershell
   pip install flask mysql-connector-python
