### SMS in Zoho Desk via Zoho flow setup

This repo is how to setup Zoho Flow and Zoho Desk so that you can send/receive SMS as a Desk ticket.

- Customer: the customer of our customer
- Agent: is the employee of our customer

## Features

- Customer sends an inbound. If this phone number didn't exist in agent's Desk contact, it will create a new contact has phone number in E.164 format
- The 1st inbound of a ticket will be a thread. All new inbounds into that ticket will be displayed as comments. The same for all outbounds.
- The phone/mobile number of the contact must be in E164 format (starts with + sign).
- If , the next inbound will

## Setup

# Zoho Desk

1. Setup layout

Go to Zoho desk setting, search for ticket layout.

Create 3 custom fields, make sure their API names are correct with the code. You can make a new section to group them

- Create a section called "SMS"
- Checkbox: "SMS Activated" (API Name: cf_sms_activated)
- Checkbox: "Send SMS" (API Name: cf_send_sms)
- Textarea: "SMS Content to send" (API Name: cf_sms_content_to_send)

"SMS Activated" is a flag being used i the code to distinguish the tickets created by SMS with created by email. So agent should never manually modify it, you should hide this field after create.

When you want to send outbound, type your outbound content to "SMS Content to send" and enable the checkbox then click Save

2. Get our org desk id

Go to Zoho desk setting > Developer space > API > scroll down to bottom.

Copy and store your Org desk id to a note, we'll use it later in Zoho Flow.

# Zoho Flow

1. Create Zoho Flow folder
   In the top-right, create a new folder. This can be named as anything.
   This folder will contains 2 flows logic for inbound and outbound.
   In the example, screenshot, the folder name is `SMS in Zoho Desk`

![zohoFlowFolder png](assets/zoho-flow-folder.png 'Create Zoho Flow folder')

2. Create inbound and outbound flow
   Inside the folder, create 2 flow, tehy can be named as anything.

The recommend name is to contain "inbound" and "outbound" in the name to distinguish the flow

![zohoFlow png](assets/zoho-flow.png 'Create inbound and outbound Flow')

3. Inbound flow

- Open the Inbound flow that you create
- Open "Builder" tab
- On the left, select tab "Logic" > "Custom functions" > "Create new custom function"
- For now you can just type any name, any parameters for the function. We will use edit feature to overwrite all after that.
  After you created the function, it will open a blank editor, just copy and paste exactly and save. You will see the new function name and parameters setup correctly

Your completed setup for INBOUND should be like this:

![inboundSetup png](assets/inbound-setup.png 'Completed setup for inbound flow')

# Message Media Hub
