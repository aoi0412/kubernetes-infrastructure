kubernetes-infrastructure/
├── infrastructure/ ← 親 Application の定義。全体の構成図
│ └── applications.yaml ← 各コンポーネントの Application 定義を集約
├── argocd/ ← ArgoCD 自体のマニフェスト群
│ ├── base/ ← デフォルト設定 (ConfigMap, RBAC, etc.)
│ ├── overlays/ ← 環境ごとの上書き設定（例：自動 sync 関連の設定とか）
│ └── application.yaml ← ArgoCD を管理するための Application 定義
└── sealed-secret/ ← Sealed Secrets の定義・設定など
├── base/
├── overlays/
└── application.yaml ← Sealed Secrets Controller を管理する Application
