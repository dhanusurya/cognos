# Determine if Report is Using an Obsolete Package

----

**1.** Navigate to the report folder.

**2.** Click the **three dots (ellipsis)** to the right of the report name.

![image](./images/bb9a3118-ff1a-4d56-8b6b-b3cf3a7676dd.png) <br>

**3.** Click **Properties** on the pop-up menu.

![image](./images/52117eaa-5e71-4a18-bd31-43ead32af207.png)<br>

**4.** When a new menu displays on the right, click to select the **Report** tab.<br>

**5.** Check the **Source** value, as shown in the screenshot below.

**a.** If the Source value = "Inventory (query)," the report will stop working when the package is retired. Please continue to the next step.<br>

**b.** If the Source value = anything *other than* "Inventory (query)," no further action is required.

![image](./images/d977348f-1daf-4354-af03-b41f0efeea2d.png)

<hr>

**6.** Determine if the report using the old package is still necessary.

**a. If the report isn't relevant anymore.**
Customers should delete it.

**b. If the report is still relevant, and customers want to continue using it.**
We encourage them to consider other current SOS reports that meet the same needs.

**c. If the report is still needed.**
Follow the [Proceed with Report Using an Obsolete Package](https://pages.github.ibm.com/SOSTeam/SOS-Docs/compliance_reporting/Cognos_Reporting/Cognos_package_replacement/) instructions.
