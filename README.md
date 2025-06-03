
# HSRS: Hierarchical Slack-Reduction Slicing for railways FRMCS

Abstract: Future Railway Mobile Communication System
(FRMCS) is a 5G network that is currently being developed
to support high-speed train mobility and growing data-rate de-
mands within the limited frequency bandwidth allocated to rail-
way operators (5–10 MHz). Network Slicing could be an essential
component of FRMCS to support different types of services:
critical (ultra-reliable, low-latency train control), performance
(video surveillance and infotainment), and business (on-board
Wi-Fi). Nevertheless, existing schedulers, designed for public 5G
Networks, assume wideband carriers or static quotas, so they
cannot guarantee per-flow service-level agreements (SLAs) or
adapt to dynamic channel-quality indicator (CQI) swings. That
is why we propose HSRS (Hierarchical Slack-Reduction Slicing),
which formulates this NP-hard allocation problem as an integer
linear program and applies a two-phase heuristic: 1) minimize
SLA slack for critical ; 2) maximize weighted throughput for
performance slice and business slice. Simulations with SNR
traces show better application-level SLA satisfaction over baseline
methods.

## Paper contribution

- We formulate FRMCS downlink scheduling problem as an ILP;
- The HSRS  heuristic design: a two-phase scheduler that (i) minimizes the “slack” of critical flows to guarantee their SLAs, and then (ii) solves a weighted rate-maximization problem to allocate remaining Resource Blocks among performance and business slices.
-  A high-fidelity evaluation: We develop a simulation environment for channel-aware RB scheduling using our Subband CQI generator, based on the first real railway high-speed train SNR dataset that captures a 350km/h train dynamic channel conditions. We compare and evaluate our approach with existing solutions.

## Code Usage
Overview of Simulation Files

In this section, we present each file used in our simulation. These files are well-commented and divided into code sections ("cells") to allow modular execution and improve readability.


## 1. Subband CQI Dataset :
 
 dataset_maker.ipynb


This is the first part of our simulator. It involves loading the SNR traces [1] of the trains from the "SNR_railways_dataset" folder. These SNR values are converted into CQI values using the mapping table proposed in 
[2]. Once the CQI values are obtained, they are plotted to visualize their variation over time for each UE (TOBA gateway).

The second step consists of generating subband CQI values based on the wideband CQI for each entry in the CSV file. The resulting subband CQI data is saved in folder named subband_cqi, which will be used in the simulation.

During the simulation, each subband CQI will be progressively injected according to its corresponding UE and the episode timeline.


## 2. Main simulation : 
HSRS.ipynb

```javascript
import Component from 'my-project'

function App() {
  return <Component />
}
```
[1] Y. Pan, R. Li, and C. Xu, “The First 5G-LTE Comparative Study in
Extreme Mobility,” Proceedings of the ACM on Measurement and
Analysis of Computing Systems, vol. 6, no. 1, pp. 1–22, Feb. 2022.

[2] A. K. Thyagarajan, P. Balasubramanian, V. D, and K. M, “SNR-CQI Mapping for 5G Downlink Network,” in 2021 IEEE Asia Pacific Conference on Wireless and Mobile (APWiMob), Apr. 2021, pp. 173–177 