# Auto-Disabled Report Schedules

> **Applies to:** IBM Cognos Analytics 12.1.3 and later

----

As of Cognos Analytics 12.1.3, the system can automatically disable report view schedules that fail consecutively. This feature prevents problematic schedules from consuming system resources indefinitely and notifies the schedule owner so the issue can be investigated and resolved.

----

## How Auto-Disabling Works

When a scheduled report fails a set number of consecutive times, Cognos Analytics automatically disables the schedule and:

- Moves it to the **Auto-Disabled** view under **Profile → My Activities and Schedules → Auto-Disabled**.
- Sends an **email notification** to the schedule owner to alert them of the failure.

The schedule will not run again until it is manually re-enabled.

----

## Configuring the Auto-Disable Threshold

The failure threshold determines how many consecutive failures are required before a schedule is automatically disabled.

**To configure the threshold (Report Administrators only):**

**1.** Go to **Profile → My Activities and Schedules → Auto-Disabled**.

**2.** Click the **threshold button** in the Auto-Disabled view.

**3.** Enter the desired threshold value:

| Value | Behaviour |
|---|---|
| **1 – 100** | Schedule is auto-disabled after this many consecutive failures |
| **0** | Auto-disabling is turned off entirely — schedules are never auto-disabled |

**4.** Save the value.

> **⚠️ Important:** The threshold applies to **all schedules** in your environment. Only Report Administrators can change it.

----

## Viewing Auto-Disabled Schedules

**1.** Click your **Profile** icon (top right).

**2.** Select **My Activities and Schedules**.

**3.** Click the **Auto-Disabled** tab.

The Auto-Disabled view lists all schedules that have been automatically disabled. You can perform the same actions here that are available for standard schedules, including re-enabling.

----

## Re-Enabling an Auto-Disabled Schedule

> **⚠️ Important:** Changing the failure threshold does **not** re-enable a schedule that has already been auto-disabled. You must re-enable it manually.

**1.** Go to **Profile → My Activities and Schedules → Auto-Disabled**.

**2.** Locate the schedule you want to re-enable.

**3.** Use the available actions to re-enable the schedule.

**4.** Before re-enabling, ensure the underlying issue that caused the failures has been resolved — for example, correcting prompt values using the [Reset Cognos Scheduler Parameters](./Cognos_scheduler_parameters_reset.md) process.

----

## Questions?

Contact the [#sos-compliance-reporting Slack channel](https://ibm-sos.slack.com/archives/C01MUGFGLEN).
