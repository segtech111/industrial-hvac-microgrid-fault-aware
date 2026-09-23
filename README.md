# Industrial HVAC–Microgrid Fault-Aware Optimization

An integrated research framework combining a real industrial AHU dataset with fault-risk monitoring, future fault-risk prediction, HVAC demand prediction, fault-aware receding-horizon optimization, and an independent islanded microgrid/BESS frequency-regulation model.

## Architecture

Real Industrial AHU Dataset → Data Quality & Temporal Alignment → Fault Monitoring & Risk Estimation → Future Fault-Risk Prediction → HVAC Demand/Energy Prediction → Fault-Aware Receding-Horizon HVAC Optimization → HVAC Electrical-Demand Coupling → Independent Islanded Microgrid Model → BESS: frequency deviation, RoCoF and SOC → Supervisory feedback

## Main implementation

- notebooks/Microgrid_Integrated_RealIndustrial_Fault_Aware_Colab.ipynb
- src/Microgrid_Integrated_RealIndustrial_Fault_Aware.py

The notebook is designed for Google Colab.

## Dataset

The raw industrial AHU dataset is intentionally not included in this public repository because redistribution permission has not been established. Place Data_Article_Dataset(1).csv in the project root for local execution, or upload it to /content/ in Colab.

## Methods

### Fault monitoring
Unsupervised anomaly detection using engineering variables and Isolation Forest. The output is a normalized operational/anomaly risk score.

### Future fault-risk prediction
Gradient-boosting regression predicts future anomaly-risk from lagged industrial AHU measurements.

### HVAC demand prediction
Gradient-boosting regression predicts next-step fan electrical demand.

### Fault-aware HVAC optimization
A receding-horizon supervisory layer evaluates outdoor-air damper, heating-water valve and chilled-water valve settings using predicted demand, comfort deviation, actuator movement and predicted fault risk.

### Microgrid/BESS model
The HVAC-derived demand is coupled to the independent islanded microgrid reduced-order model. The BESS coordinates frequency deviation, RoCoF and SOC subject to power and SOC bounds.

## Scientific boundary

The industrial dataset contains AHU/HVAC measurements; it does not provide measured microgrid frequency or BESS measurements. HVAC fault-risk and demand results are data-driven from the industrial dataset, while microgrid frequency/BESS behavior is simulated. The HVAC-to-microgrid conversion is a simulation coupling unless a calibrated site electrical base is supplied. No ground-truth fault labels are assumed.

## Outputs

The workflow generates industrial AHU, fault-risk, future-risk, HVAC demand, optimization, microgrid coupling, frequency-response, BESS-SOC and integrated-architecture figures, plus CSV/Excel result tables.

## Reproducibility

The notebook records preprocessing, chronological train/validation/test splitting, model parameters, optimization settings and exported result tables.
