# Development

## Development Summary

The Employee Onboarding & Offboarding System was developed on the **ServiceNow platform** using low-code/no-code capabilities. The implementation included:

* Created a custom **Employee Lifecycle Management** table.

* Developed **Employee Onboarding & Offboarding** Service Catalog item.

* Configured catalog variables (Employee ID, Employee Name, Department, Manager, Request Type, Joining Date, Exit Date).

* Implemented **Flow Designer** workflow.

* Configured **Manager Approval** process.

* Automated Catalog Task creation for **IT**, **Facilities**, and **Security** teams.

* Configured **Service Level Agreement (SLA)** for task tracking.

* Implemented **Role-Based ACLs**.

* Created **Reports** and **Dashboard** for HR monitoring.

* Tested complete employee lifecycle from request submission to task completion.

# Unit Testing

| Test Case ID | Module | Expected Result | Actual Result | Status |
| --- | --- | --- | --- | --- |
| UT-01 | Service Catalog | Catalog item opens successfully | Working as expected | Pass |
| UT-02 | Catalog Variables | All mandatory fields validate correctly | Working as expected | Pass |
| UT-03 | Custom Table | Employee record created successfully | Working as expected | Pass |
| UT-04 | Flow Designer | Flow triggers after request submission | Working as expected | Pass |
| UT-05 | Approval | Manager approval generated | Working as expected | Pass |

# System Testing

| Test Case ID | Scenario | Expected Result | Actual Result | Status |
| --- | --- | --- | --- | --- |
| ST-01 | Submit onboarding request | Request created | Successful | Pass |
| ST-02 | Manager approval | Approval request generated | Successful | Pass |
| ST-03 | IT Task Creation | IT catalog task created | Successful | Pass |
| ST-04 | Facilities Task Creation | Facilities catalog task created | Successful | Pass |
| ST-05 | Security Task Creation | Security catalog task created | Successful | Pass |
| ST-06 | SLA Tracking | SLA attached to catalog tasks | Successful | Pass |
| ST-07 | Dashboard | Dashboard updated with latest request | Successful | Pass |
| ST-08 | Reports | Report displays lifecycle request | Successful | Pass |

# User Acceptance Testing (UAT)

## Test Scenario

The HR Executive submitted an Employee Onboarding request through the Service Portal. The system automatically created a lifecycle request, routed it for manager approval, and after approval generated tasks for the IT, Facilities, and Security teams. Reports and dashboards reflected the request status, and SLA monitoring tracked task completion.

## UAT Results

* Employee request submitted successfully.

* Manager approval workflow executed correctly.

* Departmental tasks generated automatically.

* SLA tracking functioned correctly.

* Reports displayed request details.

* Dashboard updated with current request status.

* Overall functionality met the project requirements.

**Final UAT Status:** **PASS** ✅