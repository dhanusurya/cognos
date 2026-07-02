# Reset Cognos Scheduler Parameters

## Purpose: 

The following process helps users reset the parameters in a scheduled report view, when parameters needed by the base report have changed names due to an update.

**Customers may need to execute this process as a preemptive action after:**<br>
1. The report, that the view is based on, is updated to a new version, and <br>
2. The name, or accepted values of the parameters needed to run the report, are modified and no longer conform to the base report. 

**NOTE:** The process is also needed as a corrective action in case a scheduled report view fails following an update.  

## Process: 

**1.** Locate the report view that contains the schedule.<br>
**2.** Click the **ellipsis "..."** to the right of the name and select the **Properties** option from the dropdown menu.

![image](./images/92a595ee-253e-4926-a6fd-7e13f026b556.png)

**3.** When the next menu displays on the right, click the **Schedule** tab and **Edit** link.

![image](./images/7eda7e6f-72a7-44c0-86a4-189a08e3ae12.png)

**4.** Select the **Prompts** option in the new window to view current values.<br>
**5.** Click the **Edit prompts (_pencil icon_)** on the right side, above the **Summary** section.

![image](./images/40cc4d8b-cd75-46af-b083-03288cfb16e4.png)

**6.** When a new prompt section displays, select all the parameters needed to run the scheduled version of the report. Select the values as needed, including those required in the **Additional filters** section.<br>
**7.** Once all values have been selected, click the **Run report** button. **NOTE:** The same steps followed for running any single report.

![image](./images/cbc33537-d7c1-43eb-9660-4404025e0b57.png)

**8.** The prompts values window displays again, with the new names and values. <br>
**9.** If the selection is correct, click **Save**. The report view should be ready to resume execution. 

![image](./images/6c06b1e0-995f-4d11-8d57-98b6d8dd8a0d.png)

## Questions?:

Contact the [#sos-compliance-reporting Slack channel](https://ibm-sos.slack.com/archives/C01MUGFGLEN).
