# MPReports — Volunteer Connect Schedule Reports

This contains reports for Volunteer Connect schedules.

The RDL report files are in the `Reports` folder and the stored procedure is in the `Stored Procedures` folder. The 3 volunteer reports all use the same stored procedure.

| File | Type |
|------|------|
| `Reports/Schedule By Schedule Name.rdl` | SSRS report |
| `Reports/Schedule By Volunteer Event Time.rdl` | SSRS report |
| `Reports/Schedule Weekends With Page Breaks.rdl` | SSRS report |
| `Stored Procedures/report_Selected_Schedule_Printout_DIOSF.txt` | Shared stored procedure |

## Deploying to MinistryPlatform

After the RDL files are deployed to your SSRS report server (into an SSRS
folder — the examples below use `/MPReports/`) and the stored procedure is
created in your MinistryPlatform database, the reports still need to be made
available inside MinistryPlatform. There are three steps.

### Step 1 — Create the Report record

In **System Setup → Reports**, add a record for each report.

- **Report Name** — what staff see in the report drop-down (e.g. `Schedule By Volunteer Event Time`).
- **Report Path** — the exact path to the RDL inside SSRS, with a leading slash (e.g. `/MPReports/Schedule By Volunteer Event Time`). Spaces are allowed.
- **Pass Selected Records** — set to **Yes**. These reports run against the records the user has selected on the page.
- **On Reports Tab**, **Pass Database Connection**, **Pass Global Filter** — **No**.

![Report record — General tab](images/01-report-record-general.png)

### Step 2 — Add the Permitted Page

On the report record, open the **Permitted Pages** tab and add the page the
report launches from. For these schedule reports that is the **Schedules**
page.

![Report record — Permitted Pages tab](images/02-report-permitted-pages.png)

### Step 3 — Grant the report to a Security Role

Reports are role-based. In **Administration → Security Roles**, open the
role that should have access (e.g. **Administrators**), go to the
**Reports Permitted** tab, and add each of the three reports.

![Security Role — Reports Permitted tab](images/03-security-role-reports-permitted.png)

Once all three steps are done, refresh the Schedules page, make a selection,
and launch the report to confirm SSRS finds the RDL and the stored procedure
runs.

<a href="https://buymeacoffee.com/jwministryp" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/default-orange.png" alt="Buy Me A Coffee" height="41" width="174"></a>
