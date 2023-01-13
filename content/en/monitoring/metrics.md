---
title: Metrics
weight: 0
---

## Exported metrics

| metrics                            | type      | description                                                    | labels                          |
|:-----------------------------------|:----------|:---------------------------------------------------------------|:--------------------------------|
| **policy_total_number**            | `Guage`   | Total number of added policies                                 | policy_type                     |
| **override_policy_matched_count**  | `Counter` | The number of resources changes matched with override policies | name, resource_type             |
| **override_policy_override_count** | `Counter` | The number of resources changes override by override policies  | name, resource_type             |
| **validate_policy_matched_count**  | `Counter` | The number of resources changes matched with validate policies | name, resource_type             |
| **validate_policy_reject_count**   | `Counter` | The number of resources changes rejected by validate policies  | name, resource_type             |
| **policy_error_count**             | `Counter` | Count of error when policy engine handle policy                | name, resource_type, error_type |
| **resource_sync_error_count**      | `Counter` | Count of error when sync resource to cache                     | resource_type                   |

> To be completed...