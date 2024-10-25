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

# Legal basis for sharing data&#x20;

There are two relevant concepts here: Authentication, which represents “Who are you?” and Authorization, which in turn represents “What can you do?”. Authentication means that anyone who attempts to perform any query on an idOS node must authenticate with a wallet signature. In turn, the authorization step grants permissions to authenticated parties to do something within the idOS. This means that all queries must include a wallet signature that establishes that a certain caller controls a certain wallet and in parallel, the idOS contains rules setting forth what the parties to the network can or can not do.

A user, which in the context of the idOS is represented by at least a wallet address and an associated credential, can read from the idOS by sending it a wallet signature and what follows is that the idOS shares the encrypted data with the user who is able to read it through the signature because they own the corresponding data. Access to users’ data stored on the idOS is provided by the Access Management Protocol. To retrieve data from the idOS, users send a wallet signature, allowing the idOS to share the user’s data specific to that user.

Users issue [access grants](../../how-it-works/functionality/granting-data-access.md) that can be time-locked and are stored on a smart contract across any blockchain while the idOS monitors these smart contracts, checking for access grants and sharing data when permissions are granted. Since the data is encrypted with the users’ key that is only known to them, a copy of the data being shared via an access grant is created and subsequently encrypted with the public key of the third party being granted access to the data, who is then able to decrypt and access it for as long as the access grant is valid for or until its revocation.

When users’ data is shared with a third party in the context of an access grant, it requires the users’ agreement: Users are prompted to approve a transaction in their wallets upon granting data access to a third party and considering proper language is used, the performance of a contract between the user and the third party receiving access to the users’ data is concluded. This implies that the legal basis for the corresponding processing operation at an EU level is the performance of a contract, reflected in [Article 6 1 (b)](https://gdpr-info.eu/art-6-gdpr/) of the GDPR.&#x20;

Access grants can be set for specific durations, matching retention timelines stipulated by regulations like AML laws. This flexibility also caters to scenarios where data retention isn't mandated by law but arises from contractual terms or internal policies (the AML retention obligations' angle is further explored under [Data retention obligations](../identity-data-for-obligated-entities/data-retention-obligations.md)).&#x20;

This facilitates that third parties can continue to rely on the idOS for data access and storage, avoiding having its users’ personal data stored locally whilst keeping in line with regulatory compliance when it comes to data protection laws such as the GDPR.
