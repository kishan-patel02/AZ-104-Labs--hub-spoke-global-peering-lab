# AZ-104-Labs--hub-spoke-global-peering-lab# Azure Hub-Spoke Networking Lab (Global Peering + Free Tier Optimized)

## 📌 Overview

This lab demonstrates the implementation of a Hub-Spoke virtual network architecture in Microsoft Azure using a Free Subscription (4 vCPU limit).

The lab includes:

- Virtual Network creation
- IP address planning
- Cross-region deployment
- Global VNet Peering
- Hub-to-Spoke connectivity validation
- Understanding Azure vCPU quota limitations

---

## 🏗 Architecture

Hub VNet  
Region: East US 2  
Address Space: 10.0.0.0/16  

Spoke-App VNet  
Region: Canada Central  
Address Space: 10.1.0.0/16  

Spoke-DB VNet  
Region: Canada Central  
Address Space: 10.2.0.0/16  

Peering configured:
- Hub ↔ Spoke-App
- Hub ↔ Spoke-DB

---

## 🌍 Global VNet Peering

Because the Hub and Spokes were deployed in different regions, the architecture uses Global VNet Peering.

Azure automatically treats peering across regions as global peering. No separate configuration option is required.

This demonstrates cross-region private connectivity over the Microsoft backbone network.

---

## ⚠️ Challenge Faced – vCPU Limit

The Azure Free Subscription allows a maximum of 4 vCPUs.

Initial VM deployment attempts hit the vCPU quota limit when deploying multiple VMs in the same region.

To work within quota constraints:
- B1s VMs (1 vCPU each) were used.
- VMs were deployed strategically across regions.
- Infrastructure was optimized to stay under quota limits.

This constraint led to hands-on learning about:
- Subscription quotas
- Regional vCPU allocation
- Resource planning under limitations

---

## 🧪 Connectivity Validation

Successful ping tests confirmed:

✔ Spoke-App → Hub  
✔ Spoke-DB → Hub  
✔ Hub → Spokes  

Screenshots available in the /screenshots folder.

---

## 🧠 Key Learnings

- IP ranges must not overlap for VNet peering.
- VNet peering is not transitive.
- Cross-region peering is automatically Global VNet Peering.
- Azure subscription quotas impact architectural decisions.

# Network Design

Hub VNet: 10.0.0.0/16  
Spoke-App: 10.1.0.0/16  
Spoke-DB: 10.2.0.0/16  

Non-overlapping address spaces were used to ensure successful peering.

Hub deployed in East US 2.
Spokes deployed in Canada Central.

Cross-region connectivity validated via Global VNet Peering.
- Proper IP planning prevents deployment failures.


# Lessons Learned

1. Azure Free subscription has strict vCPU limits.
2. VM deployment failures can occur due to quota exhaustion.
3. Cross-region deployments automatically use Global VNet Peering.
4. Peering requires non-overlapping address spaces.
5. Testing connectivity using ping validates routing configuration.




---
