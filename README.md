# Framingham Risk Score -  Pooled Cohort ASCVD Risk Equations from 2013 American College of Cardiology and American Heart Association (ACC/AHA) Guideline on the Assessment of Cardiovascular Risk (CVD).

# Installation
```
pip install git+https://github.com/zhaojuanwendy/framingham.git
```

# Usage
```python
from framingham import aha_frs_cvd
frs(gender='F', age=55, tchol=213, hdlc=50, sbp=120, smoking=0, diab=0, ht_treat=False, race='W',time=10)
X = ['F', 55, 213, 50, 120, 0, 0, False, 'W', 10]
score = frs(*X)
print(score) #expected  -29.67
risk = estimate_risk(score, mean_frs=-29.18, gender='F',race='W') #expected 0.021, mean_frs is the mean frs score of the race and sex group
print(risk)
```

mean_frs is the mean frs score of the race and sex group, it can be retrived from your population sample mean. It can also be used with the recommended values from ACC/AHA.

White women, 29.18
White men, 61.18
African American women, 86.61
African American mean, 19.54

# lower risk threshold
The lower risk threshold recommended by ACC/AHA is 7.5%.
For implementation, the risk score produced by estimate_risk() is less than 7.5% is low risk of CVD.
