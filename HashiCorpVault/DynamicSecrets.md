# Static Secrets
Static secrets are secrets that are pre-defined and do not change unless explicitly modified by an administrator or authorized user.

Examples: API keys, database passwords, or encryption keys that remain constant over time unless intentionally rotated and Static configuration values that remain unchanged unless manually updated. 

Disadvantages :
1) Increased risk if compromised, as they may remain valid for extended periods.
2) Manual effort required for rotation and updating, which can introduce human error.

# Dynamic Secrets
Dynamic secrets are credentials or tokens that are generated programmatically and have a short lifespan. They are typically generated on-demand and automatically revoked after a specified time period or usage.

Examples : Temporary Access, Session Token or Short lived tokens , Temporary Service Accounts(created from automation scripts or microservices)

Advantages :
1) **Lifecycle** : They have a short lifecycle, reducing the window of exposure if compromised.
2) **Automatic Renewal** : Often, dynamic secrets are automatically renewed or rotated without manual intervention, improving security and reducing administrative overhead.
3) **Access Control** : Access to dynamic secrets is usually governed by time-based policies or other dynamic access management techniques.
4) Enhanced security through automatic expiration and rotation.
5) Reduced risk of long-term compromise due to short lifespan.
6) Automation-friendly for cloud-native and DevOps environments.

Choosing between static and dynamic secrets often depends on the specific security requirements, operational needs, and the nature of the systems and services being protected. In many cases, a combination of both static and dynamic secrets is used to balance security, usability, and operational efficiency.
