# MSF Production Monorepo

Militares Sans Frontieres (MSF) IaC Repo.

---

## Overview

This code deploys and configures my homelab environment. See [nottyxton.net](https://www.nottyxton.net) for deeper documentation on the homelab itself. I utilize a non-converged infrastructure using `Proxmox VE`, `TrueNAS Scale` and `UniFi`.

This repo enables deployment, configuration, and destruction of various components - right now mostly focused on Docker Compose. This repo is built to be declarative; leaving it as a Single Source of Truth.

### Architecture at a Glace

- **Compute:** Proxmox VE (`Raiden`) handling LXC and VM workloads
- **Storage:** TrueNAS Scale CE (`Motherbase`) with a decicate storage VLAN
- **Network:** UniFi Stack (`UCG-M`, `UX`, `16-Port-PoE-Lite`) managing strict VLAN segmentation and firewall (Trusted, Untrusted, Management, DMZ, Storage)

---

## Tools

- `Ansible` for node-level configuration

_**Soon to implement:**_

- _`Terraform` for provisioning infrastructure_
- *`Packer` for building VM OS templates using Promxox Builder

---

## Workflow

- Ansible handles all node-level resources and configurations
  - Inventory-based role assignments
  - Deploys all docker stacks and configuration files
  - Establishes API connections for Crowdsec and soon others.
  - _Goal: All plays should be strictly idempotent (actively working on this)_

---

## Disclaimers & Notes

- I am actively iterating and changing much of this repository as I fully flesh out the process. The end goal is to be able to clone this repo, point to fresh systems, and have it bring up the current state of the lab in it's entirety.

- This may not always follow best security practices, though I am working with this in mind.

- While I am working on keeping it completely idempotent it's important to note, for now, **just because it works for me, does not guarantee it will for you and your setup.**
