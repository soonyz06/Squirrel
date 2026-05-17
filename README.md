# Squirrel
- Linear models degrades gracefully as can extrapolate, while DTs suffer more as involves hard splits 
- Meta models dynamically allocates weighting to different models based on performance (risk of overfit and meta-drift)
- Drift: P(X) (OOD inputs), P(Y) (target shift), P(Y|X) (signal decay)
- Solutions: normalisation, shrinkage, retraining, detection, regime switching, online adaptation, etc
