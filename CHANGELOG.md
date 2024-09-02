# May 14th, 2024 (v1.0.1)

1. Remove for check "channel" param, use "cf_sms_activated" == "true" to allow sending outbound
2. Function `check_that_message_can_be_sent` now receive 4 params
   `map check_that_message_can_be_sent(int ticket_id, string sms_content, string send_btn_state, int desk_org_id)`
3. Add flag to append the mention assignee/team for inbound comment
4. Display the owner name in outbound comment.
5. Display the contact name in inbound comment
