---
id: prerequisites
title: Prerequisites
sidebar_label: Prerequisites
---

## Introduction
Asperato requires certain prerequisites in order to operate correctly; those prerequisites are outlined here. If you're not sure whether you can meet these prerequisites, or you need some clarification, please email support@asperato.com with any questions and we'll get back to you as soon as we can.

## Salesforce prerequisites
You must have a valid Salesforce Enterprise or Unlimited license in order to use Asperato ONE in a production setting. For testing and development purposes, Asperato ONE can also be used in a Salesforce developer org. Asperato ONE is not compatible with Salesforce Essentials or Salesforce Professional edition.

If you are using Salesforce lightning experience, then you *must* ensure that [my domain](https://help.salesforce.com/articleView?id=domain_name_overview.htm&language=en&r=https%3A%2F%2Fwww.google.co.uk%2F&type=5) is enabled and deployed to all users. You must also make sure that logins are **not** restricted to your custom domain, i.e. logins from `login.salesforce.com` (or `test.salesforce.com` for sandboxes) are still allowed.

## PSP prequisites
For live running, you must have a compatible PSP connection that has been configured to take live payments.

Note that if you are using GoCardless, you must have a GoCardless Pro account (standard and plus accounts are not supported.)
