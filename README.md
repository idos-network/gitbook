---
description: The identity layer of web3
cover: .gitbook/assets/idOS_Gitbook_hero.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 👋 Welcome to idOS

{% hint style="info" %}
**idOS (Identity Operating System) is the identity layer of web3.**\
Chain-agnostic, Compliant, Self-sovereign and Decentralized.
{% endhint %}

{% hint style="success" %}
If your are looking to integrate the idOS, please visit [dapp-sdk-integration.md](developer-docs/dapp-sdk-integration.md "mention")&#x20;
{% endhint %}

## TL;DR

#### [What is the idOS?](./#what-is-the-idos)

idOS, AKA Identity Operating System, is a decentralized storage and access management protocol designed to serve as the identity layer of web3. It aims to revolutionize the way we manage and control our digital identity and credentials in a decentralized world. Built on the principles of chain-agnosticism, compliance, self-sovereignty and decentralization, idOS empowers users to own, manage, and securely store their identity data. The idOS is [the place to store any sort of identity-related user data](overview/what-data-how-is-it-stored.md) (i.e. from KYC credentials to user social profiles) and connect it anywhere across web3.

[**Why is the idOS needed?**](overview/why-is-idos-needed.md)

In an era where data breaches, unauthorized data access, and privacy concerns are rampant, idOS addresses critical issues such as data security, user experience, and bringing new real-word use cases to web3. It offers a user-centric approach, enabling individuals to have complete control over their data without third-party intermediation. This is crucial for scalable user adoption and compliance with data protection regulations like GDPR. By focusing on the user, idOS aims to solve the challenges of identity management in a decentralized ecosystem, making it a reliable and secure choice for builders and users alike.

[**Key features of the idOS**](overview/what-is-idos.md#how-is-the-idos-different-from-existing-identity-solutions) - How is it different from existing identity solutions

1. **Chain-agnosticism**: idOS is open-source, composable and chain-agnostic. It can adapt to meet the demands of a growing user base. Its architecture is designed for composability, allowing for the integration of additional new features or already existing solutions as the system grows.
2. **Compliance**: Designed to be in line with data protection laws, idOS is a reliable choice for dApps that require compliance with data protection regulations like GDPR. It ensures that both users and businesses can navigate the complex landscape of data protection laws with ease to bring new regulated use cases to web3.
3. **Self-sovereign data management**: Users have the autonomy to view, add, share, and revoke access to their data and credentials. They can manage their identity in a self-sovereign manner, free from third-party control.
4. **Decentralization**: idOS utilizes a dStorage Network of Nodes to ensure data availability, even when the user is offline (unlike with identity wallets). This decentralized approach enhances data security and availability, making it resilient against centralized points of failure.

[**The idOS Consortium**](overview/the-idos-consortium.md)

The idOS is a joint effort and backed by leading ecosystems **Arbitrum** Foundation, **Circle** (through its affiliate Circle Ventures), **Ripple**, **NEAR Foundation**, **Gnosis**, **Aleph Zero** Foundation, **Radix** and the **Tezos** Foundation (Etherlink). These partners actively contribute to the development, adoption, and scalability of the idOS, enhancing its utility and reach. Each partner brings unique capabilities and expertise to the table, enriching the idOS ecosystem and ensuring user adoption. Do you want to contribute to the future of identity? Come build with us!

[**System architecture**](how-it-works/system-architecture/)

idOS is composed of two main elements: a [dStorage Network of Nodes](how-it-works/system-architecture/decentralized-storage/) and an [Access Management Protocol](how-it-works/functionality/granting-data-access.md). These components work in tandem to provide a secure and efficient identity management system. The idOS also offers an [SDK for dApps](developer-docs/dapp-sdk-integration.md) to integrate seamlessly and a [User Data Dashboard](how-it-works/functionality/user-data-dashboard.md) for users to manage their stored data. This architecture is the backbone of the idOS, ensuring that it can deliver on its promise of secure, decentralized identity management.

[**Roles and Data Flows in the idOS**](how-it-works/system-architecture/roles-main-stakeholders.md)

* **Users**: Users are at the center of the idOS ecosystem. They can view, add, share, and revoke access to their data. All identity data is encrypted by default by the user before being added to the idOS, ensuring maximum security. Users have full control over who has access to their data, making the idOS a truly user-centric and self-sovereign system.
* **dApps (across different blockchain ecosystems)**: Decentralized applications can request data access from users and can check that the data provided by the user has been verified by a trusted credential provider or data verifier. This enables dApps to offer personalized or regulated services without compromising user privacy.
* **Node operators**: Node operators host the idOS' encrypted data and execute the idOS dStorage Network of Nodes. They enforce access rights and block unauthorized access, ensuring that only authorized entities can access user data. Node operators are the custodians of (encrypted) user data, playing a crucial role in maintaining the integrity and security of the idOS.
* **Identity verification providers**: Data providers supply verified data in the W3C verifiable credential standard. They play a crucial role in the idOS by helping users to add verified data to their profiles. Data providers and verifiers add value to the idOS ecosystem by ensuring that the data within the idOS is reliable and trustworthy.

[**Data structure & Schema**](broken-reference)

While it is possible to add any type of data into the nodes, idOS encourages and empowers verified data to be stored as [W3C Verifiable Credentials](how-it-works/system-architecture/decentralized-storage/w3c-verifiable-credentials.md). Data is structured in the form of a [relational database](how-it-works/system-architecture/decentralized-storage/database-overview.md) utilizing Kwil's infrastructure.

[**Security and Encryption**](how-it-works/encryption.md)

idOS follows high standards of encryption to ensure data security. All identity data stored is user-encrypted before being added to idOS, and it is stored in a decentralized manner across multiple nodes. idOS employs state-of-the-art encryption algorithms to secure user data, making it one of the most secure identity management systems available.

[**Progressive Decentralization**](how-it-works/progressive-decentralization.md)

idOS has a roadmap for progressive decentralization. It plans to deploy across multiple decentralized chains, ensuring scalability and security. By adopting a multi-chain approach, idOS aims to become a universal identity layer that can be integrated into various blockchain ecosystems. This progressive decentralization strategy ensures that idOS remains agile and adaptable, ready to meet the challenges of a rapidly evolving digital landscape.



**Quick links:**

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}
