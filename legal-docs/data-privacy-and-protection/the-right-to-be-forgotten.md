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

# The right to be forgotten&#x20;

The 'right to be forgotten' is established under [Article 17](https://gdpr-info.eu/art-17-gdpr/) of the GDPR at an EU level but is also present in other data protection laws around the globe, such as the [California Consumer Privacy Act (CCPA)](https://oag.ca.gov/privacy/ccpa). Focusing on GDPR, the latter states that data subjects shall have the right to obtain the erasure of personal data concerning them without undue delay if one of the situations described under the first number of the article applies, such as when the personal data are no longer necessary in relation to the purposes for which they were collected or otherwise processed, or when the data subject withdraws consent on which the processing is based, for example.&#x20;

Although the idOS in itself is merely a platform that allows for data processing operations to take place, it has an embedded mechanism in place to allow users to delete the data being stored on their private profiles.

Once a user requests the deletion of their data via the [User Data Dashboard](../../how-it-works/functionality/user-data-dashboard.md), the idOS will check the information available in the smart contract it monitors for the existence of any access grants related to such data that are currently still valid for a pre-determined amount of time. If no valid access grant is found, the consensus mechanism comes in to ensure the deletion of the user’s data within the network: If a certain node does not store, update, or delete data when they are supposed to, it is impossible for that node to continue being a validator within the network. If the node then tries to propose a block, this can result in getting the node’s stake slashed and as nodes also cannot properly validate blocks, they cannot trust any new data added.

This means that the idOS engine imposes a strict requirement that each database is the same and so within the network, every block, and each node proves back to the network what their current state is. Making an analogy with a math problem, If the nodes have the correct data, which in the case of a deletion request is that they have deleted the correct data, it is very easy to solve the math problem. However, If the nodes don’t have the right data, it is essentially impossible to solve, and perpetually solving this problem is a requirement to continue being a validator within the network.

Unlike most decentralized networks, there is no option for a “soft fork”, and there is one definitively correct answer at every block. The answers build on each other and if a node doesn’t get the last answer right, it also won’t be able to get the next one right (even if it got the previous correct answer from another node).

However, If after checking the smart contract the idOS indeed finds a valid access grant currently standing for the user data that is subject to the deletion request, meaning that it is currently still valid or for a pre-determined amount of time, as the user’s data being shared is duplicated upon the creation of an access grant and re-encrypted with the viewer keys, the idOS allows the user to delete the encrypted data that is stored in the idOS for which only the user knows the keys for, via the consensus mechanism explained above.

In turn, the data that is encrypted with the viewer keys is not included in the deletion request, meaning this third-party viewer would continue to have access to it, until the expiration of the access grant. Currently, no automatic deletion of the data encrypted with the viewer keys takes place, but potentially this will change to allow users to set an automatic deletion of such data upon expiration of the access grant.

If an access grant in turn is not time-bound and the user requests to delete data previously shared under this access grant, the data (both the original data as well as the duplicated data that is encrypted with the viewer keys) will be deleted in accordance with the consensus mechanism outlined above.&#x20;
