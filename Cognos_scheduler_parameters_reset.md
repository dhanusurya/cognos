# Reset Cognos Scheduler Parameters

## Purpose:

The following process helps users reset the parameters in a scheduled report view, when parameters needed by the base report have changed names due to an update.

**Customers may need to execute this process as a preemptive action after:**<br>
1. The report, that the view is based on, is updated to a new version, and <br>
2. The name, or accepted values of the parameters needed to run the report, are modified and no longer conform to the base report.

**NOTE:** The process is also needed as a corrective action in case a scheduled report view fails following an update.

> **⚠️ Cognos Analytics 12.1.3+:** If the report view schedule has failed repeatedly, it may have been automatically disabled by the system. Before starting this process, check **Profile → My Activities and Schedules → Auto-Disabled** to see if the schedule is listed there. You will need to re-enable it after correcting the prompt values.

---

## Process:

**1.** Locate the report view that contains the schedule in your **Team content** or **My content** folder.<br>

**2.** Click the **Actions menu icon (⋮)** to the right of the report view name and select **Properties** from the dropdown menu.

![image](./images/92a595ee-253e-4926-a6fd-7e13f026b556.png)

> 📸 *Screenshot requires replacement — the Actions menu icon (⋮) appearance and Properties panel layout changed in Cognos Analytics v12.x.*

**3.** In the **Properties panel** that opens on the right side of the screen, click the **Schedule** tab. Then click the **Edit** link next to the existing schedule.

![image](./images/7eda7e6f-72a7-44c0-86a4-189a08e3ae12.png)

> 📸 *Screenshot requires replacement — Properties now opens as a collapsible side panel, not a full-page form.*

**4.** In the schedule editor, click the **Prompts** tab to view the currently saved prompt values for this scheduled entry.<br>

**5.** Click the **Set values** link to open the prompt selection interface.

![image](./images/40cc4d8b-cd75-46af-b083-03288cfb16e4.png)

> 📸 *Screenshot requires replacement — the pencil icon has been replaced by a **Set values** text link in v12.x.*

**6.** When the prompt selection interface opens, select all the parameters needed to run the scheduled version of the report. Select the values as needed, including those required in the **Additional filters** section.<br>

**7.** Once all values have been selected, click **Done** to apply the prompt values to the schedule.

![image](./images/cbc33537-d7c1-43eb-9660-4404025e0b57.png)

> 📸 *Screenshot requires replacement — the prompt selection panel in the schedule context shows a **Done** button, not a Run report button.*

**NOTE:** Clicking **Done** applies the selected values to the schedule configuration — it does **not** run the report immediately. The report view will execute at its next scheduled time.

**8.** The **Prompts** section of the schedule now displays the updated parameter names and values.<br>

**9.** Review the values shown in the **Summary** pane on the right. If the selections are correct, click **Save**. The report view schedule will be updated and the report will run with the new prompt values at its next scheduled time.

![image](./images/6c06b1e0-995f-4d11-8d57-98b6d8dd8a0d.png)

> 📸 *Screenshot requires replacement — confirm the Save button and updated Prompts summary reflect the v12.x schedule editor layout.*

---

## Questions?:

Contact the [#sos-compliance-reporting Slack channel](https://ibm-sos.slack.com/archives/C01MUGFGLEN).
