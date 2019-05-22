---
description: You can apply budget alerts to either a billing account or a project.
---

# Set Budget Alerts

You can set the budget to an amount you specify or match it to the previous month's spend. When costs \(actual costs or forecasted costs\) exceed a percentage of your budget, based on the rules you set, alert notifications are sent to billing administrators and billing account users \(that is, every user assigned a [billing role](https://cloud.google.com/iam/docs/understanding-roles#billing-roles) of either `roles/billing.admin` or `roles/billing.user`\).

> **Important:** Setting a budget does **not** cap API usage. The purpose of budgets is to allow you to trigger alert notifications so that you know how your spending is trending over time. Budget alerts prompt you to take action to control your costs, but do not prevent the use or billing of your services when the budget is met or exceeded.

## Create a budget

The budget amount you set is used to calculate the thresholds that trigger sending alert notifications. The budget does not set a hard cap on spending.

To create a budget:

1. Go to the [Google Cloud Platform Console](https://console.cloud.google.com/).
2. Open the console left side menu \(menu\) and click **Billing**.
3. If you have more than one billing account, select **Go to linked billing account** to manage the current project's billing. To locate a different billing account, select **Manage billing accounts**.
4. On the left, click **Budgets & alerts**.
5. Click add\_box **CREATE BUDGET** \(near the top of the page\).
6. Under **Budget name** enter a name for the budget.
7. Under **Project or billing account**, select the project or the billing account that you want to apply the budget alert to. If you apply a budget alert to a billing account, the alert reflects the spending across all projects associated with the billing account.
8. Under **Budget amount** you can choose to set the budget to a **Specified amount** or you can set it to match **Last month's spend**. \(Note that the monthly spend resets to $0 on the first day of every month.\)
9. If you're setting the budget to a specified amount, enter that amount. If you're basing the budget on the previous month's spend, the amount updates automatically.
10. Optionally, you can choose to enable **Cost after credit**. Cost after credit is the total cost minus any applicable credit\(s\). Credits may include usage discounts, promotions, and/or grants to use Google Cloud Platform.
11. **Set budget alerts**: To set or remove budget alert threshold rules, proceed to the next task, _Set, edit, or remove budget alert threshold rules_. If you want to accept the default alert threshold rules, click **Save**.

## Set, edit, or remove budget alert threshold rules

To set, edit, or remove budget alert threshold rules:

1. If necessary, [create a budget](https://cloud.google.com/billing/docs/how-to/budgets#create-budget) as described above. Or, to add alerts to an existing budget, open the budget to be updated:
   1. Go to the [Google Cloud Platform Console](https://console.cloud.google.com/).
   2. Open the console left side menu \(menu\) and click **Billing**.
   3. If you have more than one billing account, select **Go to linked billing account** to manage the current project's billing. To locate a different billing account, select **Manage billing accounts**.
   4. On the left, click **Budgets & alerts**, then click the name of the budget that you want to update with alert threshold rules.
2. Go to the **Set budget alerts** section. When you first create a budget, the default alert thresholds are set at 50%, 90%, and 100% of the budget amount, calculated against actual spend. You can modify the percentages and the type of spend, and add or remove alert threshold rules.
3. Under **Percent of budget**, enter the percent of the budget at which you want an alert triggered. The corresponding spend **Amount** is filled in automatically. \(Alternatively, if you prefer, you can enter the **Amount** and let Google fill in the percentage for you.\)
4. Under **Trigger on**, select either **Actual** or **Forecasted** spend.
   * **Actual** cost threshold rules send notifications when the cumulative cost accrued during the budget period exceeds the threshold amount. For example, if you set a 50% actual spend alert on a $100 budget, then you will receive an alert notification when you have spent $50 during the budget period.
   * **Forecasted** cost threshold rules send notifications when the forecasted cost \(calculated out to the end of the current budget period\) exceeds the threshold amount. For example, if you set a 110% forecasted cost alert on a $100 budget, then you will receive an alert notification when you are forecasted to spend more than $110 by the end of the budget period.
5. To add additional alert threshold rules, click add**Add item** below the list of current alert threshold rules.
6. To remove a threshold rule, click the clear icon to the right of the row you want to remove.
7. To save the current budget alerts settings, click **Save**.

