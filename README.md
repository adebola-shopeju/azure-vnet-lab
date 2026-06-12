# Azure Virtual Network Lab – Three‑Tier Network with NSGs

**Lab 7**: VNet with web, app, and database subnets, NSGs, and connectivity tests.

## Architecture

| Tier | Subnet       | Address range | NSG      | Public IP | Allowed inbound            |
|------|--------------|---------------|----------|-----------|----------------------------|
| Web  | subnet-web   | 10.0.1.0/24   | nsg-web  | Yes       | HTTP(80), HTTPS(443)       |
| App  | subnet-app   | 10.0.2.0/24   | nsg-app  | No        | (default rules only)       |
| DB   | subnet-db    | 10.0.3.0/24   | nsg-db   | No        | Only from 10.0.2.0/24      |

## Screenshots

All screenshots are in the `/screenshots` folder.

- `VNet_Overview.png` – VNet address space and region
- `VNet_Deployment_Complete.png` – VNet creation complete
- `All_Subnets_Created.png` – Three subnets with correct CIDR ranges
- `All_NSGs_Created.png` – Three NSGs created
- `NSG_Web_Rules.png` – Allow HTTP/HTTPS, deny all other inbound
- `NSG_App_Rules_.png` – No extra inbound rules
- `NSG_DB_Rules.png` – Only allow app subnet (10.0.2.0/24)
- `VM_Web_Deployed.png` – vm-web-01 deployment
- `VM_Web_Running.png` – vm-web-01 running
- `VM_App_Deployed.png` – vm-app-01 deployment
- `Both_VMs_Running.png` – Both VMs running
- `ping-test.png` – Successful ping from web → app (10.0.2.4)
- `ping-web-to-db-blocked.png` – **Blocked** ping from web → db (10.0.3.4)

## Validation

- ✅ Web ↔ App: ping succeeds  
- ✅ App ↔ DB: ping succeeds (tested from app VM)  
- ✅ Web → DB: ping **fails** (NSG on db subnet correctly denies)

## Cleanup

To avoid charges, delete the resource group `rg-vnet-lab-eastus` from Azure Portal.
