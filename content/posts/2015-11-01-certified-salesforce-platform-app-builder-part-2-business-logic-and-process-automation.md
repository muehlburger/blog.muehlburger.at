---
title: 'Certified Salesforce Platform App Builder – Part 2: Business Logic and Process Automation'
author: Herbert Mühlburger
type: post
date: 2015-11-01T11:29:12+00:00
draft: true
url: /?p=2113
bitcointips_address:
  - 1DGHB1RwBMebHaUdNBpLXxqr8qTEFTiy1B
categories:
  - Consulting
  - HowTo
  - Salesforce
tags:
  - Business Logic and Process Automation
  - Salesforce
  - Salesforce Certified Platform App Builder Exam

---
## Business Logic and Process Automation (27 %)

This topic is the most important one in the &#8220;Certified Salesforce Platform App Builder&#8221; exam. You can expect to get around 17 questions on topics such as Record Types, Formula Fields, Roll-Up Summary Fields, Validaton Rules, Approval Processes, &#8230;

The following table gives an overview on the parts of &#8220;Business Logic and Process Automation&#8221;:

<table width="598">
  <tr>
    <td width="424">
      <strong>Topic</strong>
    </td>
    
    <td width="87">
      <strong>Weight</strong>
    </td>
    
    <td width="87">
      <strong>Questions</strong>
    </td>
  </tr>
  
  <tr>
    <td>
      <strong>Business Logic and Process Automation</strong>
    </td>
    
    <td>
      <strong>27%</strong>
    </td>
    
    <td>
      <strong>16,2</strong>
    </td>
  </tr>
  
  <tr>
    <td style="padding-left: 30px;">
      Record Types
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Formula Fields
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Roll-Up Summary Fields
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Validation Rules
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Approval processes
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Workflow, Visual Workflow and Lightning Process Builder
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Automate Business Processes
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
  
  <tr style="padding-left: 30px;">
    <td style="padding-left: 30px;">
      Ramifications of Field Updates and the potential for Recursion
    </td>
    
    <td style="padding-left: 30px;">
    </td>
    
    <td style="padding-left: 30px;">
    </td>
  </tr>
</table>

### Record Types

Record types can be used to control three things:

<p style="padding-left: 30px;">
  a) Business processes<br /> b) Page layouts<br /> c) Picklist values
</p>

  * Record types tailor user interaction experience to specific business needs
  * Record types determine page layouts
  * Record types limit picklist values (options)
  * Record types only affect the way that data is displayed on the user interface. They are not a form of sub-classing.

### Formula Fields

There are two types of Formula Fields

<p style="padding-left: 30px;">
  a) Custom formula fields<br /> b) Cross-Object formula fields
</p>

#### Custom Formula fields

Can reference standard, custom, or other formula fields

Can reference fields on related objects

Are calculated when the field is accessed

Necessary steps to implement formula fields:

  1. Define business case
  2. Create simple statement
  3. Translate simple statement to formula example:

<pre>IF(ISPICKVAL(Status__c, “Open”), 24*(NOW() – CreatedDate), null))</pre>

#### Cross-Object Formulas

  * Create formulas that reference fields on parent and grandparent object (up to 10 levels)
  * Limited to ten unique relationships per object across all formulas and rules for that object
  * Display fields from related objects on detail pages, list views, reports, …

### Roll-Up Summary Fields

### Validation Rules

### Approval Processes

### Workflow, Visual Workflow and Lightning Process Builder

### Automate Business Processes

### Ramifications of Field Updates and the potential for Recursion

##