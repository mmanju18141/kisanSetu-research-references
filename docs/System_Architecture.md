# Proposed system architecture

This document describes a practical architecture for the Kisan Setu prototype. It is a design outline, not a statement that every component has already been built.

## Main layers

### 1. User interface

A simple web or mobile interface where a farmer can enter crop details, review available prices, compare options and approve or reject proposed actions. The interface should use clear language, work on lower-end devices where possible and be designed for regional-language support.

### 2. Application backend

The backend manages user sessions, validates inputs, applies access rules and coordinates requests between the interface, data services and decision-support modules.

### 3. Data layer

The data layer stores only information needed for the service. This may include farmer-entered crop details, saved comparisons, verified buyer quotations and records of consent. External market information should retain its source, timestamp, location, crop, grade and unit where available.

### 4. Decision-support services

Calculations such as estimated net return, storage cost and repayment impact should be implemented as deterministic functions with tests. The AI agents may explain the results, but should not invent missing values or silently change calculation assumptions.

### 5. AI agent layer

The four planned agents are Price Watch, Sell-or-Store, Storage and Credit, and Coordination. Each should have a limited role and access only to the information required for its task. Any action that affects the outside world must pass through an approval step.

## Example data flow

1. The farmer enters crop, quantity and location details.
2. The application retrieves or displays available price information from approved sources.
3. The farmer adds a buyer quotation or confirms relevant costs.
4. The calculation service compares the available options and records its assumptions.
5. An agent explains the comparison in plain language and identifies missing information.
6. The farmer reviews the result and decides what to do.
7. If the farmer asks to contact a buyer or service provider, the system prepares the message and requests approval before sending it.

## Security and privacy considerations

- Collect the minimum information needed for a feature.
- Keep secrets and API keys outside source control.
- Use authentication and role-based access where accounts are supported.
- Protect personal and financial information in transit and at rest.
- Record consent and important actions in an audit trail.
- Do not share farmer information with third parties without clear permission.
- Provide a way to correct or remove information where appropriate.

## Reliability considerations

Market information can be delayed, incomplete or inconsistent. The interface should show timestamps and source details, identify stale data and avoid presenting an estimate as a confirmed offer. If a source is unavailable, the system should say so rather than quietly substitute an unsupported value.
