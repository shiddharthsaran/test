flowchart TD
  A[_generate_realistic_transaction]
  
  %% Dates
  A --> B[Generate transaction_date & account_open_date]
  
  %% Amount
  A --> C[_generate_realistic_amount]
  C --> C1[Priority decision]
  C1 --> C2[High: 85% large 100k–500k, 15% small overlap 5k - 10k]
  C1 --> C3[Moderate: 80% med-high 20k–100k, 20% small 5k - 15k]
  C1 --> C4[Low: 85% 5k–20k, 15% smaller 2k - 5k]
  C1 --> C5[Normal: 95% 10–5k, 5% higher 5k - 10k]

  %% Customer risk score
  A --> D[_generate_realistic_risk_score]
  D --> D1[Priority decision]
  D1 --> D2[High: μ=90, σ=5]
  D1 --> D3[Moderate: μ=72, σ=7]
  D1 --> D4[Low: μ=50, σ=6]
  D1 --> D5[Normal: μ=30, σ=10]

  %% Transaction risk score
  A --> E[_generate_realistic_transaction_risk_score]
  E --> E1[Priority decision]
  E1 --> E2[High: Beta 5, 1.5]
  E1 --> E3[Moderate: Beta 3, 2]
  E1 --> E4[Low: Beta 2, 3]
  E1 --> E5[Normal: Beta 1.5, 5]

  %% Country
  A --> F[_select_country]
  F --> F1[Priority decision]
  F1 --> F2[High: 85% high-risk, 15% normal]
  F1 --> F3[Moderate: 30% high-risk, 70% normal]
  F1 --> F4[Low: 10% high-risk, 90% normal]
  F1 --> F5[Normal: 100% normal]

  %% Business type
  A --> G[_select_business_type]
  G --> G1[Priority decision]
  G1 --> G2[High: 80% high-risk, 20% normal]
  G1 --> G3[Moderate: 40% high-risk, 60% normal]
  G1 --> G4[Low: 10% high-risk, 90% normal]
  G1 --> G5[Normal: 100% normal]

  %% Transaction type
  A --> H[_select_transaction_type]
  H --> H1[Priority decision]
  H1 --> H2[High: 75% high-risk, 25% normal]
  H1 --> H3[Moderate: 40% high-risk, 60% normal]
  H1 --> H4[Low: 10% high-risk, 90% normal]
  H1 --> H5[Normal: 100% normal]

  %% Daily count
  A --> I[_generate_realistic_daily_count]
  I --> I1[Priority decision]
  I1 --> I2[High: 85% 16–30, 15% 5–15]
  I1 --> I3[Moderate: 70% 10–20, 30% 5–15]
  I1 --> I4[Low: 30% 8–15, 70% 1–10]
  I1 --> I5[Normal: 1–8]

  %% Monthly count
  A --> J[_generate_realistic_monthly_count]
  J --> J1[Priority decision]
  J1 --> J2[High: 85% 201–350, 15% 100–200]
  J1 --> J3[Moderate: 70% 150–250, 30% 50–150]
  J1 --> J4[Low: 30% 100–180, 70% 10–100]
  J1 --> J5[Normal: 1–100]

  %% Binary flags
  A --> K[_generate_realistic_binary_flags]
  K --> K1[Priority decision]
  K1 --> K2[High: 3–5 flags]
  K1 --> K3[Moderate: 85% 1–3 flags]
  K1 --> K4[Low: 30% 1 flag]
  K1 --> K5[Normal: 10% 1 flag]

  %% Combine
  A --> L[Combine all fields into record]
  L --> M[Return final transaction dict]

  %% Styling
  classDef decision fill:#FEF3C7,stroke:#333,stroke-width:1px;
  class C1,D1,E1,F1,G1,H1,I1,J1,K1 decision;
