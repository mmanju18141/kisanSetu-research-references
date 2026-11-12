# Planned AI agent workflow

The agents in Kisan Setu are intended to assist with separate tasks. They should work from information available to the platform, explain uncertainty and ask for approval before taking any external action.

## 1. Price Watch Agent

**Purpose:** Help the farmer review available market price information.

**Inputs:** Selected crop, market or location, date range and available price records.

**Work:** Organises the records, points out changes and flags missing or old entries. It keeps source and timestamp information attached to the result.

**Output:** A short price summary with the markets covered, dates, units and any data limitations.

**Boundary:** It must not claim that a reported market price is a guaranteed buyer offer or make up missing prices.

## 2. Sell-or-Store Agent

**Purpose:** Explain the financial differences between available choices.

**Inputs:** Quantity, current offer, known costs, storage duration and charges, crop condition, cash requirement and any confirmed deductions.

**Work:** Calls the project's calculation functions to compare scenarios such as selling now, storing, or selling part of the produce. It explains the assumptions and highlights values that are unknown.

**Output:** A comparison of estimated outcomes, not a guaranteed prediction of future prices.

**Boundary:** It should not tell a farmer to wait for a price increase as if that increase were certain. Calculations must be traceable and testable outside the language model.

## 3. Storage and Credit Agent

**Purpose:** Help the farmer review storage and credit-related information.

**Inputs:** Crop, location, quantity, intended storage period and verified information about facilities or finance terms.

**Work:** Organises available facility details, lists costs that need confirmation and prepares questions for the provider or lender.

**Output:** A shortlist or checklist with source, date and details that still need confirmation.

**Boundary:** It cannot guarantee storage availability, loan eligibility, approval or a particular interest rate.

## 4. Coordination Agent

**Purpose:** Reduce the effort involved in contacting relevant organisations.

**Inputs:** Farmer-approved enquiry details and the selected buyer, FPO, warehouse or service provider.

**Work:** Drafts a clear message containing only the information the farmer has chosen to share.

**Output:** A message for the farmer to review.

**Boundary:** The message must not be sent until the farmer explicitly approves it. The agent must not accept offers, place orders or make commitments on the farmer's behalf.

## Shared approval process

1. The agent prepares a suggestion or message.
2. The application shows the farmer exactly what information will be used or shared.
3. The farmer can edit, approve or cancel.
4. Only after approval does the application perform the permitted action.
5. The system records what was approved and what happened.

## Handling uncertain information

If information is missing, old or unverified, the agent should say so. It should ask for confirmation where necessary and avoid presenting guesses as facts. For important calculations, the system should show the inputs used so that the result can be checked.
