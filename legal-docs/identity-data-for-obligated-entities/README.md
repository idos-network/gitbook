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

# Identity data for obligated entities

The idOS has some key features and mechanisms that make it a robust tool for AML compliance. It supports the storage of verified KYC/AML data and in its initial integration with foundational partners, such as Fractal ID, as well as the possibility of other identity providers becoming a part of the idOS, allows for users' identity data to undergo verification before being stored on the idOS, providing financial institutions with a reliable source of verified identity information, which is crucial for AML compliance.

Data stored within the idOS is encrypted using unique self-generated keys and its distributed node storage system ensures data availability even if one node is compromised, adding an extra layer of resilience.

The idOS Access Management Protocol, which is underpinned by blockchain technology, provides a transparent record of data access permissions, ensuring traceability, another key component of AML compliance. At the same time, the [User Data Dashboard](../../how-it-works/functionality/user-data-dashboard.md) interface allows users to manage their data actively so financial institutions can guide their users to interact with this dashboard to provide access to their KYC/AML data, ensuring that data access is up-to-date. The idOS' chain-agnostic nature ensures that it can integrate seamlessly with various blockchain platforms and such flexibility allows financial institutions to incorporate the idOS into their existing systems without being tied to a specific blockchain.

The idOS also uses CometBFT, which aims to ensure that all nodes in the network maintain a consistent state of data, fostering an environment where the KYC/AML data accessed by financial institutions is consistent across the network. The idOS was also designed to allow users to update, add, or remove data from their accounts, meaning the most recent and accurate version of a credential can always be easily shared with institutions upon a new access grant. This can help the institutions to have the latest information on their users, vital for example, in the context of AML checks.

All in all, the idOS provides a secure, transparent, and efficient platform for storing and accessing verified identity data, making it a valuable tool for financial institutions to meet their AML obligations. Its commitment to data integrity, user control, and regulatory alignment contributes that financial institutions trust the idOS as a reliable partner in their AML compliance journey.
