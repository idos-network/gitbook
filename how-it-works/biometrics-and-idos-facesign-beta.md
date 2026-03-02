# idOS FaceSign

idOS FaceSign is a wallet you can't lose. It lets users authenticate, sign, and prove who they are across any idOS-powered application, using nothing but a two-second video-selfie. No wallets. No passwords. No seed phrases to lose. Just you.

150,000+ users have created an idOS Profile with idOS FaceSign across the idOS ecosystem, with partners like Billions, Ready, and Tally actively rolling out idOS FaceSign to their users. idOS FaceSign isn't a prototype — it's privacy-preserving identity infrastructure live at scale.

## What is idOS FaceSign?

idOS FaceSign is an all-encompassing authentication feature built on idOS that lets users do three things with their face:

**Log in to any idOS-integrated application.** No wallet connection required. A quick liveness-proven video-selfie on any device returns a signing key that authenticates you, just like a wallet would — except you can't lose it, forget it, or have it stolen.

**Prove uniqueness.** idOS FaceSign generates a cryptographic proof that you are a unique person in the system, without exposing your biometric data to any application or developer. This enables sybil resistance, one-person-one-vote, and duplicate account detection — all without sacrificing privacy.

**Carry your identity across apps.** Once you have an idOS profile with idOS FaceSign, the credentials issued to you — Proof of Personhood, KYC, and more — travel with you. Log in to one app with your face, and your verified identity is available everywhere, controlled entirely by you.

## How it works

1. Your device captures a short 3D video-selfie.
2. The capture is encrypted and sent directly to a TEE (Trusted Execution Environment), ensuring that not even idOS has access to it.
3. The TEE processes the video-selfie into a [3D FaceMap](https://dev.facetec.com/facemap-3d) — an opaque binary blob that captures the three-dimensional geometry of your face. Only FaceTec's software can interpret a FaceMap. You cannot reconstruct a face from a FaceMap; you can only match FaceMaps against each other.
4. The first time the TEE sees your face, it uses a cryptography-grade entropy source to generate a random signing key for you.
5. The raw video-selfie is discarded. Only the matching result (new user or existing) and the derived key material leave the enclave. No photos, images, or raw biometric data are ever stored or retained.

### User flow

1. **You capture on your own device.** You take a short video-selfie on your phone or laptop.
2. **Encrypted handoff to a secure compute enclave.** The captured data is sent over an encrypted channel to a locked-down [AWS Nitro Enclave](https://docs.aws.amazon.com/enclaves/latest/user/nitro-enclave.html). Before running any matching code, it generates a [3D FaceMap](https://dev.facetec.com/facemap-3d) — an opaque, non-reversible biometric representation that contains no photos or images. Nitro Enclaves are isolated VMs with **no external networking and no interactive access**.
3. **Compute-only result leaves the enclave.** The enclave computes whether you are **new** or **already known** and outputs only an anonymized unique user ID with linked entropy for key derivation. The raw selfie frames are not persisted.
4. **No data, images, or video are stored.** No sensitive biometric data is stored anywhere.
5. **You receive a Verifiable Credential (VC)** with a unique idOS biometric ID in your idOS profile. The credential is encrypted with your keys, and stored in idOS. You control who can decrypt it via Access Grants.

## What's stored in the enclave

Only one type of biometric data is stored inside the enclave: **FaceMaps**.

FaceMaps are opaque binary blobs produced by FaceTec's software. They are not photos. They are not images. You cannot reconstruct a face from a FaceMap — you can only match FaceMaps against each other. FaceMaps are what power idOS FaceSign's core features: uniqueness checks, authentication, and key derivation.

When you take a video-selfie to log in or prove you're unique, your FaceMap is matched against existing records inside the enclave. No human ever sees or reviews this data. It's machine-to-machine matching, and the only outputs are a yes/no result and derived key material.

idOS stores no raw biometric data. No photos. No images. No video frames. No selfies. The video-selfie you take during an idOS FaceSign session is processed in real time inside the enclave, converted into a FaceMap, and discarded. The raw biometric input never persists — not in the enclave, not on our servers, not anywhere. What remains is a mathematical representation that cannot be reversed into anything resembling your face.

Nobody can access any of this data — not even us. The enclave has no external networking, no SSH, and no shell. Communication with the enclave is only possible through predefined interfaces. Developers can only interact with specific endpoints — like checking if a user is unique, or authenticating them with their face. The enclave outputs results, never biometric data of any kind.

## Privacy by design

* **Biometric capture happens on _your_ device.** You record a short video-selfie locally, with your own personal device. There's no third-party or shared hardware involved.
* **No human/operator access before, during, or after biometric compute.** The matching step runs inside [Nitro Enclaves](https://docs.aws.amazon.com/enclaves/latest/user/nitro-enclave.html), which **cannot be SSH'd into** and **don't expose a network interface**. Data is processed in enclave memory and not viewable by admins or support staff.
* **No photos of your face are matched or stored.** Before any matching takes place, a [3D FaceMap](https://dev.facetec.com/facemap-3d) is generated — an opaque binary blob, not a photo. Actual video frames are permanently deleted inside the secure enclave once the FaceMap is created.
* **No photos stored in idOS; only an encrypted credential with your unique ID.** After matching, you are prompted to store a **Verifiable Credential** containing the anonymized unique ID — **not** the selfie, frames, or templates. The credential remains **encrypted with your keypair**, and third parties can only read it if **you grant access**.
* **Multiple profiles, with a user-controlled "same-person" proof.** At a protocol level, you may have more than one idOS profile (e.g., for pseudonymous contexts). Because the **same issuer-signed VC** can be held from more than one profile, **you** can later prove those profiles are controlled by the **same person**.

## Security at the core

* **Isolated biometric compute.** User deduplication and matching runs inside [**AWS Nitro Enclaves**](https://docs.aws.amazon.com/enclaves/latest/user/nitro-enclave.html) — isolated VMs with **no external networking and no shell access**, even to a root admin on the host.
* **Encrypted credentials at rest.** idOS stores credentials already [encrypted to the user's keys](https://docs.idos.network/how-it-works/key-flows/encryption-flows), and access to contents requires a user-granted **Access Grant** to a specific consumer address. Current SDKs use [**x25519-xsalsa20-poly1305**](https://docs.idos.network/how-it-works/key-flows/encryption-flows) authenticated encryption.
* **Powered by FaceTec.** The biometric engine is built on [FaceTec's 3D Face Authentication](https://www.facetec.com/), which reports a False Acceptance Rate **(FAR) of 1 in 125,000,000** at less than 1% False Rejection Rate (FRR) in its [official accuracy report](https://www.facetec.com/FaceTec_3D_Face_Matching_Whitepaper.pdf). It has passed [independent PAD testing (ISO/IEC 30107-3)](https://facetec.com/FaceTec_BixeLab_3D_PAD_Test_Report_v1.0.pdf). There is a [**live, public spoof bounty of $600K**](https://dev.facetec.com/spoof-bounty-program) for anyone that can defeat its liveness and capture defenses.

FaceMaps enable 3D:3D matching at 1/125,000,000 FAR (the highest confidence level), 3D:2D matching against photo IDs for privacy-preserving identity checks, and cross-organization interoperability for credential portability.

## What you're trusting

We want to be precise about this.

* **Us, in the immediate term.** Right now, you are trusting that the idOS FaceSign enclave is set up and operates as we describe. We are telling you that nobody — including us — can access the data inside the enclave, and that the only way to interact with it is through predefined endpoints. In the near term, this is a trust-us claim.
* **AWS and Intel.** You are trusting that AWS's Nitro Enclave hardware isolation works as advertised — that the dedicated hardware with no persistent storage, no administrator access, and no interactive debugging is genuinely isolated. You are also trusting that there are no hardware-level exploits in the underlying Intel silicon. Even Amazon cannot access the data inside a running enclave, by design.
* **Our operational security.** You are trusting that we do not leak our AWS credentials, which would allow a malicious actor to push different code to the enclave that behaves differently than advertised.
* **FaceTec.** You are trusting that FaceTec's closed-source binary — which runs inside the enclave and handles the core biometric processing — behaves as advertised. That there are no backdoors, no secret data exfiltration, and no "phoning home." The binary is a black box. We cannot inspect its internals, and neither can you. This is a real trust assumption that we take seriously and aim to mitigate over time.

## Making idOS FaceSign more trust-minimized

We are not asking you to take idOS FaceSign's security on faith. Our roadmap is focused on systematically reducing trust assumptions and increasing verifiability:

**Enclave attestation logs (near-term).** We are working to publish attestation logs and the full build process for all idOS FaceSign code that runs inside the enclave. Nitro Enclaves support cryptographic attestation — the enclave can produce a signed proof of its code and configuration, verifiable by third parties. One important caveat: even with attestation logs, fully reproducing the build chain requires access to FaceTec's proprietary software. We expect to publish as much as possible, and may work with independent auditors — in cooperation with FaceTec — to provide additional assurance.

**Execution proofs (long-term).** True execution proofs — cryptographic proof that the computation itself ran correctly — are a different and harder problem. As long as FaceTec's binary is closed-source, full execution proofs are not feasible. To get there, we would need to build or migrate to an open-source replacement for FaceTec's biometric engine. This is on our long-term radar but is not imminent.

**Removing the single point of failure (long-term).** Today, idOS FaceSign runs on a single TEE provider. Our long-term direction is to remove this dependency — first by exploring redundancy across TEE providers, and more ambitiously, by exploring an MPC quorum architecture where no single TEE holds the full sensitive material.

The end goal: a system where you don't have to trust us, you don't have to trust any single cloud provider, and the only remaining trust assumption is the biometric engine itself — which we aim to make open-source and independently auditable.

## idOS FaceSign for developers

{% hint style="info" %}
Developer documentation for idOS FaceSign integration is coming soon. Contact the idOS team at developers@idos.network for early access.
{% endhint %}

Developers will have two paths to integrating idOS FaceSign:

1. **Direct integration with the idOS FaceSign SDK.** For teams that want full control, you'll be able to integrate the idOS FaceSign SDK directly into your application and call the idOS FaceSign frontend enclave endpoints yourself. This gives you maximum flexibility over the user experience and flow design.

2. **Managed service via idOS Relay.** For teams that want a turnkey solution, idOS Relay — operated by Fractal ID, idOS's KYC orchestrator — provides an iframe-based flow that handles the idOS FaceSign session, uniqueness verification, KYC orchestration, and credential issuance in a single, hosted experience. idOS Relay enforces data deletion for providers, does not store any data past 14 days, and standardizes outputs into the shared Verifiable Credential schema.

Here's what you'll be able to build:

* **Passwordless, walletless authentication.** Integrate idOS FaceSign as your primary login mechanism. Users authenticate with a video-selfie — no wallet extension, no seed phrase, no password reset flow.
* **Sybil resistance and uniqueness.** Use idOS FaceSign to gate access to features that require one-person-one-account: airdrops, governance votes, free trials, community rewards. The uniqueness proof is privacy-preserving and doesn't require you to handle any biometric data.
* **KYC re-usability.** Accept Verifiable Credentials issued by other idOS-integrated applications. When a user logs in with idOS FaceSign, check whether they already hold a valid KYC credential — and if so, skip the entire verification flow.
* **Age and attribute verification.** Request specific credential attributes (e.g., "is this person over 18?") without accessing the full identity document.
* **Biometric 2FA and account recovery.** Add idOS FaceSign as a second factor for high-value transactions, or as a recovery mechanism for users who lose access to their primary wallet.
