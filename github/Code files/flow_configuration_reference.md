# Flow Configuration Reference

**Flow name:** Standard laptop task
**Application scope:** Global
**Run As:** System User
**Status:** Active

This document is a structured reference of the ServiceNow Flow Designer flow
built for this project. It is provided as the closest equivalent to source
code for a no-code/low-code automation, so the configuration can be reviewed
or reproduced without direct access to the ServiceNow instance.

---

## Trigger

```
Trigger type : Service Catalog
```

The flow starts whenever the Service Catalog trigger condition is met for a
request against the associated catalog item (see Assignment section below).

---

## Action 1 — Create Catalog Task

```
Action        : Create Catalog Task
Table Name    : Catalog Task [sc_task]   (auto-populated)

Inputs:
  Requested Item  <- Trigger.Service Catalog.Requested Item Record

Field values set on the new Catalog Task record:
  Short description  = "Laptop need to Configured"
  Description        = "Laptop need to Configured"
  Assignment group   = "Hardware"
  Approval           = "Approved"

All other fields: left at ServiceNow defaults.
```

### Field mapping summary (table form)

| Target field (sc_task)  | Source / Literal Value                     |
|--------------------------|---------------------------------------------|
| Table Name                | Catalog Task [sc_task] (auto-populated)     |
| Requested Item             | Trigger → Service Catalog → Requested Item Record |
| Short description          | Literal: "Laptop need to Configured"        |
| Description                 | Literal: "Laptop need to Configured"        |
| Assignment group            | Literal: "Hardware"                          |
| Approval                    | Literal: "Approved"                          |

---

## Catalog item assignment (Process Engine)

```
Catalog Item : Standard Laptop
Category     : Hardware
Process Engine:
  Flow            = Standard laptop task
  Workflow        = (cleared)
  Execution Plan  = (cleared)
```

This ensures the "Standard laptop task" flow is the sole automation engine
governing fulfilment of the Standard Laptop catalog item — no competing
Workflow or Execution Plan is active on the same item.

---

## Pseudocode equivalent

For reference, the flow's logic expressed as pseudocode:

```
ON Service Catalog request event (for Standard Laptop item):
    requested_item = trigger.requested_item_record

    catalog_task = CREATE record IN sc_task:
        requested_item      = requested_item
        short_description    = "Laptop need to Configured"
        description           = "Laptop need to Configured"
        assignment_group      = "Hardware"
        approval               = "Approved"

    SAVE catalog_task
END
```

---

## Notes

- This flow does not call any external API, script include, or business
  rule; all logic is contained within the two components above (trigger +
  single action).
- No custom scripting (JavaScript) was used inside the flow — every value
  is set declaratively through Flow Designer's field-mapping interface.
