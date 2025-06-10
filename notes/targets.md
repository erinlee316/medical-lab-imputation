In clinical lab trajectories, very few biomarkers exhibit strictly monotonic behavior over time under natural, unmanipulated physiological conditions. Most lab values exhibit some degree of fluctuation due to homeostatic regulation, measurement noise, disease progression, or interventions. However, certain biomarkers are *typically* monotonic in specific clinical contexts—especially when disease is progressing without treatment. Here are some notable examples:

### **Monotonic Decreasing Trends**

* **GFR (Glomerular Filtration Rate)**: In chronic kidney disease (CKD), GFR generally exhibits a **monotonic decline** over time, reflecting worsening renal function. While it may fluctuate acutely (e.g., in AKI or volume depletion), the *longitudinal trend* in CKD is almost always downward unless an intervention (e.g., dialysis or transplant) occurs.

* **Hemoglobin in chronic bleeding or advanced CKD**: In the context of untreated anemia (e.g., GI bleed or EPO deficiency in CKD), hemoglobin can show a monotonic decrease. However, it is susceptible to intervention and therefore not globally monotonic.

* **Albumin in progressive liver failure or malnutrition**: Serum albumin can show a gradual decline in cirrhosis, nephrotic syndrome, or protein-energy malnutrition, although acute-phase responses and IV albumin can induce fluctuations.

### **Monotonic Increasing Trends**

* **Creatinine (inverse of GFR)**: In CKD, serum creatinine tends to **monotonically increase**, although it is sensitive to muscle mass, hydration status, and medications (e.g., trimethoprim).

* **HbA1c in uncontrolled diabetes**: Over months, in the absence of glycemic control, HbA1c typically increases, though it's measured intermittently and not sensitive to short-term fluctuations.

* **Prostate-Specific Antigen (PSA)** in untreated prostate cancer or BPH: Can show monotonic increase, though it is quite noisy.

* **Ferritin in iron overload syndromes**: In hereditary hemochromatosis or repeated transfusions, ferritin can rise steadily, but it is also an acute-phase reactant and can jump during inflammation.

### **Monotonicity with Contextual Caveats**

Many lab values are **conditionally monotonic** in certain trajectories:

* **INR** in chronic liver disease or under stable warfarin dosing can increase over time.
* **Lactate** in unresolving sepsis will rise monotonically but typically changes acutely.
* **BUN** in volume depletion or progressing CKD often rises, but not always steadily.

### **Conclusion**

True strict monotonicity is rare outside of controlled experimental conditions or end-stage disease processes. However, **GFR and Creatinine** are the clearest real-world examples of approximately monotonic decline/increase respectively in the context of **progressive CKD**. For modeling purposes, you might consider “nearly monotonic” markers—those with a high signal-to-noise ratio in one direction over a relevant disease timescale. These are useful for trajectory learning, disease staging, and survival modeling when filtered through clinical context and proper preprocessing.
