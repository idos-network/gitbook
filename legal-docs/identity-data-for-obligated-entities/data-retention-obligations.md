---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Data retention obligations

Understanding the intricacies of data retention, especially in the context of AML obligations, is crucial for any financial institution. Within the idOS framework, when a user provides access to their KYC data via an access grant, the duration of this access can be previously set. This predetermined period allows for alignment with the necessary retention periods for compliance, ensuring that the data remains accessible for the required timeframe.

At the same time, while the idOS is built on the principle of user self-sovereignty, allowing users to manage their data, there are built-in safeguards to ensure compliance. If a user wishes to delete a piece of data, the idOS checks for any active access grants associated with that data. If an access grant with a set time period is active, the idOS will restrict the user from deleting the duplicated and re-encrypted data until the grant expires (but at the same time, allowing for the deletion of the original user data encrypted with the unique key only known to the user, as further explained under [The right to be forgotten](../data-privacy-and-protection/the-right-to-be-forgotten.md)). This mechanism ensures that data remains intact and accessible for the duration necessary for AML and other compliance obligations.

As access grants within the idOS can come with an immutable time log, they ensure transparency and provide a clear record of when access was granted as well as the duration of access. Such a feature can be crucial in the context of audit trails and regulatory checks.

While the idOS empowers users with control over their data, it recognizes also the importance of regulatory compliance. In the context of AML obligations, data generally cannot be arbitrarily deleted. Even if a user wishes to delete their KYC data, the idOS' built-in mechanisms, considering active access grants and their durations, ensure that data remains available for the necessary retention periods while allowing for alignment with data protection standards.&#x20;

The decentralized nature of the idOS, with its dStorage Network of Nodes, ensures data availability and resilience. Even if a node is compromised, the data remains accessible across the network, and coupled with user[ encryption](../../how-it-works/encryption.md) and the consensus mechanism, this ensures data availability.

Once a user has given access to its encrypted data stored on the idOS via an access grant within the Access Management Protocol, the third-party viewer is able to access it, decrypt the corresponding data, and decide whether to keep it stored internally or not. In this context, the idOS aims to strike a balance between user control and regulatory compliance: By integrating the idOS, institutions have consistent access to KYC data and can comply with data retention obligations without compromising on user privacy or data security.&#x20;
