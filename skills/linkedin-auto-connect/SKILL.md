---
name: linkedin-auto-connect
description: Sends personalized connection requests from LinkedIn people search results. Use this when the user wants to expand their professional network by bulk-sending customized connection messages based on a template, with daily rate limiting to avoid account restrictions.
triggerPhrases:
  - linkedin批量加好友
  - send linkedin connection requests
  - linkedin自动连接
  - bulk connect linkedin
  - linkedin群发邀请
startUrl: "https://www.linkedin.com/search/results/people/"
urlPattern: "linkedin.com"
categories:
  - social
  - automation
parameters:
  - name: message_template
    type: string
    description: "Connection request message template — use {{name}} for the person's name and {{headline}} for their job title"
    required: true
  - name: daily_limit
    type: number
    description: "Maximum number of connection requests to send in this session to avoid LinkedIn rate limits"
    required: false
    default: 20
preconditions:
  - type: url_contains
    value: "linkedin.com"
    description: "Browser must be on LinkedIn domain with active login session"
---

# LinkedIn Smart Connect

## Workflow
1. Navigate to https://www.linkedin.com/search/results/people/ (LinkedIn People Search).
2. For each person in the search results (up to {{daily_limit}} people):
   a. Extract their display name and headline text.
   b. Click the "Connect" button next to their profile.
   c. In the connection modal, click "Add a note".
   d. Fill in the message field using {{message_template}}, replacing {{name}} with their name and {{headline}} with their headline.
   e. Click "Send" to submit the request.
   f. Wait 3-5 seconds before processing the next person.
3. If more results exist and the daily limit is not reached, scroll down or click "Next" to load more profiles.

## Preconditions
- User must be logged into their LinkedIn account (active session).
- Browser must be on the LinkedIn domain to ensure session cookies are available.
- The search results page should already be filtered to the desired audience.

## Success Criteria
- Connection requests are sent to up to {{daily_limit}} people from the search results.
- Each message is personalized with the recipient's name and headline.

## Notes
- Profiles that already show "Pending" or "Message" (already connected) are automatically skipped.
- If LinkedIn shows a CAPTCHA or rate limit warning, the skill stops immediately to protect the account.
- The 3-5 second delay between requests mimics human behavior to reduce detection risk.
- Message template must be under 300 characters (LinkedIn's limit for connection notes).
