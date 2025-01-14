---
title: "Fix email delivery issues for error code 550 5.1.1 through 5.1.20 in Exchange Online"
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 
ms.reviewer: 
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
ms.custom: MiniMaven
search.appverid:
- BCS160
- MOE150
ms.assetid: 79e91ade-5c83-405b-a37d-d99c7d069b13
description: "Learn how to fix email issues for error code 5.1.1 through 5.1.20 in Exchange Online (the recipient doesn't exist or your Auto-Complete list entry for the recipient is bad)."
---

# Fix email delivery issues for error code 550 5.1.1 through 5.1.20 in Exchange Online

It's frustrating when you get an error after sending an email message. This topic describes what you can do if you see error codes 550 5.1.1 through 5.1.20 in a non-delivery report (also known as an NDR, bounce message, delivery status notification, or DSN).

|||||
|:-----|:-----|:-----|:-----|
|![Email user icon](../../media/31425afd-41a9-435e-aa85-6886277c369b.png)|[I got this bounce message. How do I fix it?](#i-got-this-bounce-message-how-do-i-fix-it)|![Email admin icon](../../media/3d4c569e-b819-4a29-86b1-4b9619cf2acf.png)|[I'm an email admin. What can I do to fix this?](#im-an-email-admin-what-can-i-do-to-fix-this)|

## I got this bounce message. How do I fix it?

Here are some steps that you can try to fix the problem yourself.

If the steps in this section don't fix the problem for you, contact your email admin and refer them to the information in this topic so they can try to resolve the issue for you.

### Solution 1: Confirm the recipient's email address

It sounds too simple, but the wrong email address is the most common issue that causes 5.1.x errors. Check for correct spelling and send the message again if you find an error in the email address.

To resend the message in Outlook, see [Resend an email message](https://support.office.com/article/acd16ac4-c881-477d-b4aa-36168fa96088.aspx).

### Solution 2: Remove the recipient's email address from your Auto-Complete list

You might have an invalid entry in your Auto-Complete list (also known as the _nickname cache_) for the recipient. For example, the recipient might have been moved from an on-premises Exchange organization to Exchange Online, or vice-versa. Although the recipient's email address is the same, other internal identifiers for the recipient might have changed, thus breaking your cached entry for the recipient.

#### Fix your Auto-Complete list entries in Outlook

To remove invalid recipients or all recipients from your Auto-Complete list in Outlook 2010 later, see [Manage suggested recipients in the To, Cc, and Bcc boxes with Auto-Complete](https://support.office.com/article/dbe46e31-c098-4881-8cf7-66b037bce23e).

#### Fix your Auto-Complete list entries in Outlook on the web

To remove recipients from your Auto-Complete list in Outlook on the web (formerly known as Outlook Web App), do one of the following procedures:

##### Remove a single recipient from your Outlook on the web Auto-Complete list

1. In Outlook on the web, click **New mail**.

2. Start typing the recipient's name or email address in the **To** field until the recipient appears in the drop-down list.

   ![Screenshot shows the Send Again option for an email message. In the Resend to field, the AutoComplete feature provides the email address for the recipient based on the first few letters typed of the recipient's name.](../../media/409b56f4-1a7f-417e-94cf-9a058ac851d4.png)

3. Use the Down Arrow and Up Arrow keys to select the recipient, and then press the Delete key.

##### Remove all recipients from your Outlook on the web Auto-Complete list**

You can only clear your Auto-Complete list in the light version of Outlook on the web. To open your mailbox in the light version of Outlook on the web, do either of the following steps:

- Open the mailbox in an older web browser that only supports the light version of Outlook on the web (for example, Internet Explorer 9).

- Configure your Outlook on the web settings to only use the light version of Outlook on the web (the change takes effect the next time you open the mailbox):

   1. In Outlook on the web, click **Settings** ![Settings icon](../../media/f4b2e798-fff1-4a14-931f-5677a4543b58.png).

   2. In the **Search all settings** box, type **light** and select **Outlook on the web version** in the results.

   3. In the page that opens, select **Use the light version of Outlook on the web**, and then click **Save**.

   4. Log off, close your web browser, and open the mailbox again in Outlook on the web.

After you open your mailbox in the light version of Outlook on the web, do the following steps to clear all entries from your Auto-Complete list:

1. Choose **Options** and verify that **Messaging** is selected.

2. In the **E-Mail Name Resolution** section, click **Clear Most Recent Recipients list**, and then click **OK** in the confirmation dialog box.

3. While you're still in **Options**, to return your mailbox to the full version of Outlook on the web, go to **Outlook version**, clear the check box for **Use the light version**, and then click **Save**.

4. Log off and close your web browser. The next time you open your mailbox in a supported web browser, you'll use the full version of Outlook on the web.

To remove invalid recipients or all recipients from your Auto-Complete list in Outlook 2010 later, see [Manage suggested recipients in the To, Cc, and Bcc boxes with Auto-Complete](https://support.office.com/article/dbe46e31-c098-4881-8cf7-66b037bce23e).

### Solution 3: Confirm that the recipient isn't auto-forwarding messages from you to another (and likely, invalid) email address

Does the recipient's email address in your original message exactly match the recipient's email address in the NDR? Compare the recipient's email address in the NDR with the recipient's email address in the message in your **Sent Items** folder.

If the addresses don't match, contact the recipient (by phone, in person, etc.) and ask them if they've configured an email rule that forwards incoming email messages from you to another destination. Their rule could have tried to send a copy of your message to a bad email address. If the recipient has such a rule, they'll need to correct the destination email address or remove the rule in order to prevent 5.1.x message delivery errors.

### Solution 4: Verify that your account hasn't been compromised

Did you send the original message at all? If not, it's possible that a spammer or hacker inappropriately used your account to send the message.

Check your recent messages in the **Sent Items** folder for strange or unknown messages (messages that you didn't send). If you find any, it's possible that your email account was compromised.

If you believe that your account has been compromised, follow these steps:

- Reset your password and scan your devices for malware. However, the hacker might have configured other settings on your mailbox (for example, created Inbox rules to auto-forward email messages or added additional mailbox delegates). So, follow the additional steps in [How to determine whether your Office 365 account has been compromised](https://go.microsoft.com/fwlink/p/?linkid=861995).

- Notify your email admin. Your admin will need to unblock your account before you can send email again.

### Solution 5: Confirm that the NDR is related to a message that you actually sent

If your **Sent** folder contains only messages that you know you sent, then the NDR you received could be a result of _backscatter_ (a useless NDR about a message you didn't send), and you can ignore it.

Typically, if a message can't be delivered, the recipient's email system will use the sender's email address in the **From** field to notify the sender in an NDR like this one. But what if the message was sent by a spammer who falsified the **From** address so it appears the message came from your email address? The resulting NDR that you'll receive is useless because it creates the false impression that you did something wrong. This type of useless NDR is called _backscatter_. It's annoying, but if this NDR is backscatter, your account hasn't been compromised.

Check your recent messages in the **Sent Items** folder for strange or unknown messages (messages that you didn't send). If you don't see any suspicious messages, it's likely that the NDR you received is backscatter. If you've already changed your password and run an anti-malware scan, you can ignore these backscatter NDRs.

To learn more, see [Backscatter messages and EOP](https://technet.microsoft.com/library/dn499795.aspx).

## I'm an email admin. What can I do to fix this?

If the steps in the previous section don't solve the issue for the sender, the solution might be related to the way the user's Office 365 account is set up. If you have a hybrid topology, the solution might also be related to the on-premises mail transfer agent. It might also be a problem with the recipient's domain configuration. Here are 4 solutions you can try. You might not need to try all of them to get the message sent successfully.

### Solution 1: Check the Office 365 Message Center for configuration problems or service-wide issues

For Office 365 accounts, the Office 365 portal provides a central source for a variety of tools, notifications, and information that you can use to troubleshoot this and other issues.

Log in to an administrator account on the Office 365 portal at [https://portal.office.com](https://portal.office.com), and from the **Dashboard**, do the following:

1. Check the **Message Center** to see if your organization has a known configuration issue.

   1. Choose **Message center**.

   2. Select **View all**.

   3. Select **Prevent or fix issues**, and perform any relevant suggested actions.

2. Check if there's a current service issue in Office 365 affecting the user's account.

   1. Choose **Service health** to see an overview of any issues.

   2. Select **View all** to get more details about all known issues.

3. Check the sender and recipient domains for incorrect or stale mail exchange (MX) resource records by running the [Mailflow Troubleshooter](https://docs.microsoft.com/exchange/mail-flow-best-practices/troubleshoot-mail-flow) tool that is within Office 365.

If there's a problem with the recipient's domain, contact the recipient or the recipient's email administrator to let them know about the problem. They'll have to resolve the issue in order to prevent NDR 5.1.x errors.

### Solution 2: Update stale MX records

Error code 5.1.1 can be caused by problems with the MX resource record for the recipient's domain. For example, the MX record might point to an old email server, or the MX record might be ambiguous due to a recent configuration change.

> [!NOTE]
> Updates to a domain's DNS records can take up to 72 hours to propagate to all DNS servers on the Internet.

If external senders (senders outside your organization) receive this NDR when they send message to recipients in your domain, try the following steps:

- The MX resource record for your domain might be incorrect. The MX record for an Exchange Online domain points to the email server (host) _\<domain\>_.mail.protection.outlook.com.

- Verify that you have only one MX record configured for your Exchange Online domain. We don't support using more than one MX record for domains enrolled in Exchange Online.

- Test your MX record and your ability to send email from your Exchange Online organization by using the **Verify MX Record and Outbound Connector Test** at **Office 365** \> **Mail Flow Configuration** in the Microsoft Remote Connectivity Analyzer.

For more information, see [Create DNS records at any DNS hosting provider for Office 365](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) and [Set up SPF in Office 365 to help prevent spoofing](https://docs.microsoft.com/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing).

### Solution 3: Update forwarding rules to remove incorrect email addresses

This NDR might be caused by a forwarded (unintended) recipient that's configured for the intended recipient. For example:

- A forwarding Inbox rule or delegate that the recipient configured in their own mailbox.

- A mail flow rule (also known as a transport rule) configured by an email admin that copies or forwards messages sent to the recipient to another invalid recipient.

For more information, see [Configure email forwarding for a mailbox](https://technet.microsoft.com/library/dd351134.aspx).

## Still need help with error code 5.1.1 to 5.1.20?

[![Get help from the Office 365 community forums](../../media/12a746cc-184b-4288-908c-f718ce9c4ba5.png)](https://go.microsoft.com/fwlink/p/?LinkId=518605)

[![Admins: Sign in and create a service request](../../media/10862798-181d-47a5-ae4f-3f8d5a2874d4.png)](https://go.microsoft.com/fwlink/p/?LinkId=519124)

[![Admins: Call Support](../../media/9f262e67-e8c9-4fc0-85c2-b3f4cfbc064e.png)](https://go.microsoft.com/fwlink/p/?LinkID=518322)

## See also

[Email non-delivery reports in Office 365](non-delivery-reports-in-exchange-online.md)
