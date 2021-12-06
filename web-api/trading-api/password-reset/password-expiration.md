---
description: Update expired passwords via API
---

# Password Expiration

### Overview

In ETNA Trader, the broker may have configured a security policy whereby users' passwords automatically expire after a certain period. After expiration of their password, if a trader attempts to [log in](../authentication/) via API, they will receive a token that should later be used in this endpoint to update the expired password.
