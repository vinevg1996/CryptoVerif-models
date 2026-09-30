# CryptoVerif Models for (Singularized) Password-Authentication Protocols

This repository contains CryptoVerif models for two password-authentication protocol variants:

- `pwd_with_enc_without_singularization.cv` — baseline password-authentication protocol.
- `pwd_with_enc_with_singularization.cv` — singularized password-authentication protocol.

The models are intended to compare the computational security bounds obtained for the baseline and singularized protocol variants.

## Requirements

To run the models, install **CryptoVerif**.

CryptoVerif is available from:

https://bblanche.gitlabpages.inria.fr/CryptoVerif/

Follow the installation instructions provided on the CryptoVerif website.

## Running the Models

### Baseline Password-Authentication Protocol

Run:

```bash
./cryptoverif pwd_with_enc_without_singularization.cv
```

The expected security bound is:

```text
Pr[Game 1: second_preimage_found]
  <= (qH + 2) * Pcoll1rand(passwd_t)
     + Penc(time_1, 1)
     + (2 + qH) / |hashed_passwd_t|
```

This bound expresses the probability of the event `second_preimage_found` in terms of the security assumptions associated with the underlying cryptographic primitives.

### Singularized Password-Authentication Protocol

Run:

```bash
./cryptoverif pwd_with_enc_with_singularization.cv
```

The expected security bound is:

```text
Pr[Game 1: hash_preimage_found]
  <= (qH + 1) / |G|
     + PExpToGroup
     + (2 + qH) / |hashed_passwd_t|
```

This bound additionally contains terms associated with the group-based operations introduced by the singularized protocol.

## Contact

For questions about the models, please contact:

**Evgenii Vinarskii**  
vinarskii.evgenii@telecom-sudparis.eu
