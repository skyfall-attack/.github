<p align="center">
  <a href="https://skyfall-attack.github.io/">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/skyfall-attack/.github/main/profile/assets/skyfall-logo-dark.svg">
      <img src="https://raw.githubusercontent.com/skyfall-attack/.github/main/profile/assets/skyfall-logo-light.svg" width="112" height="112" alt="SKYFALL — a CPU leaking data">
    </picture>
  </a>
</p>

<h1 align="center">SKYFALL</h1>
<p align="center">
  <strong>Microarchitectural Data Sampling on AMD</strong><br>
  IEEE Symposium on Security and Privacy (S&amp;P), 2027
</p>
<p align="center">
  <a href="https://skyfall-attack.github.io/"><strong>Website</strong></a> ·
  <a href="https://skyfall-attack.github.io/assets/skyfall.pdf"><strong>Paper</strong></a> ·
  <a href="https://skyfall-attack.github.io/#systems"><strong>Affected systems</strong></a> ·
  <a href="https://skyfall-attack.github.io/#faq"><strong>FAQ</strong></a>
</p>

## Overview

SKYFALL is a microarchitectural data sampling attack on AMD processors. It allows privileged software to recover sensitive data across isolation boundaries protecting confidential virtual machines, microcode, and System Management Mode memory.

We show that AMD’s cache way predictor uses its µtag address hash for physical and CPU-internal addresses as well as virtual addresses. Combined with incomplete predictor-state cleanup, these collisions let an attacker sample residual cache data using Transient Scheduler Attacks (TSA-L1).

## What we demonstrate

| Target | Demonstrated leakage |
| --- | --- |
| **SEV-SNP confidential VMs** | Guest register state through an aborting VMRUN, including a controlled disk-encryption key recovery demonstration, and guest memory at three fixed cache-line offsets within a selected page. |
| **Microcode updates** | Decrypted patch contents on all three tested systems; the pre-EntrySign CMAC key on the tested EPYC 7313. |
| **System Management Mode** | Protected State Save Area fields, including SMBASE, CR3, and R13. |

See the [project website](https://skyfall-attack.github.io/) for the attack mechanism, experimental conditions, tested systems, and FAQ.

## Disclosure

We reported our findings to AMD, which assigned **CVE-2026-40671**. See the [website’s FAQ](https://skyfall-attack.github.io/#faq) for mitigation information.

## Authors

[Benedict Schlüter](https://benschlueter.com/)\*, [Alessandro Vezzù](https://www.linkedin.com/in/avezzu/)\*, [Daniel Moghimi](https://moghimi.org/), and [Shweta Shinde](https://www.shwetashinde.org/).

ETH Zurich and Google. \* Equal contribution.

## Citation

```bibtex
@inproceedings{schlueter2027skyfall,
  title = {{SKYFALL}: Microarchitectural Data Sampling on {AMD}},
  author = {Schl{\"u}ter, Benedict and Vezz{\`u}, Alessandro and
            Moghimi, Daniel and Shinde, Shweta},
  booktitle = {2027 IEEE Symposium on Security and Privacy (SP)},
  year = {2027},
  publisher = {IEEE}
}
```
