# Methodology

## Industrial AHU data
The raw AHU measurements are converted to a 15-minute temporal grid. Short gaps are interpolated within the configured limit. Engineering features include zone-temperature statistics, total fan power, outdoor-air fraction and thermal residuals.

## Fault-risk monitoring
Standardized engineering variables are processed with Isolation Forest. The training distribution defines the normalization reference for a 0–1 operational anomaly/fault-risk score.

## Future fault-risk prediction
Lagged AHU measurements are used to predict a shifted future anomaly-risk score. This is prediction of future operational anomaly risk, not verified physical fault occurrence.

## HVAC demand prediction
A supervised gradient-boosting regression model predicts next-step fan electrical demand from current and lagged AHU variables.

## Fault-aware HVAC optimization
A short-horizon supervisory optimizer evaluates outdoor-air damper, heating-water valve and chilled-water valve candidates using predicted demand, comfort deviation, actuator movement, simultaneous heating/cooling activity and predicted risk.

## Microgrid coupling
The optimized HVAC signal is converted to an equivalent normalized disturbance for the independent islanded microgrid model. Unless a calibrated site electrical base is available, this is a simulation interface rather than measured electrical conversion.

## BESS frequency regulation
The independent reduced-order model uses frequency deviation, filtered RoCoF and SOC feedback with bounded BESS power and SOC. Controller cases include baseline/no BESS, frequency droop, frequency+SOC and frequency+RoCoF+SOC.
