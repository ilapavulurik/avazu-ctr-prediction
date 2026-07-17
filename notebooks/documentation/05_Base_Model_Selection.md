
# Base Model Selection
```mermaid
flowchart TD

    A[Prepared Encoded Data] --> B[500K Training Sample]
    A --> C[100K Validation Sample]

    B --> D[StandardScaler]
    D --> E[Logistic Regression]
    C --> E

    E --> F["Logistic Regression Results<br/>Log Loss: 0.40169<br/>ROC-AUC: 0.65108"]

    B --> G[HistGradientBoosting]
    C --> G

    G --> H["Best Model<br/>HistGradientBoosting<br/>Log Loss: 0.37606<br/>ROC-AUC: 0.73080"]

    F --> I{Compare Validation Results}
    H --> I

    I --> J[Select HistGradientBoosting]

    J --> K["Additional Metrics<br/>PR-AUC: 0.32096<br/>Precision: 0.57878<br/>Recall: 0.05018"]

    K --> L[Threshold and Calibration Analysis]

    classDef best fill:#d5f5e3,stroke:#1e8449,stroke-width:3px;
    classDef baseline fill:#ebf5fb,stroke:#2874a6,stroke-width:2px;
    classDef warning fill:#fdebd0,stroke:#ca6f1e,stroke-width:2px;

    class H,J best;
    class E,F baseline;
    class K,L warning;
```mermaid    