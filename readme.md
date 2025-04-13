argocd/
├── base/
│ ├── kustomization.yaml
│ └── manifests.yaml # ArgoCD の公式マニフェスト（controller, server など）
├── overlays/
│ └── default/
│ ├── kustomization.yaml
│ ├── argocd-cm.yaml # 設定 ConfigMap（UI の設定など）
│ ├── clusters-secrets.yaml
│ ├── repos-secrets.yaml
│ └── argocd-params.yaml # その他カスタム用
├── application.yaml # ArgoCD を自己管理する Application リソース
└── kustomization.yaml # 上位の kustomization（通常は overlays を指定）

infrastructure/
├── applications.yaml 👈 Application 定義（argocd/や sealed-secret/を指す）
└── kustomization.yaml 👈 これは applications.yaml だけを参照

sealed-secret/
├── base/
│ ├── kustomization.yaml
│ ├── controller.yaml # controller のマニフェスト（URL でも OK）
│ └── public-cert.pem # 公開鍵（任意、kubeseal に使う）
├── overlays/
│ └── default/
│ ├── kustomization.yaml
│ ├── argocd-cluster-sealed.yaml # ← clusters-secrets.yaml を sealed にしたもの
│ └── argocd-repo-sealed.yaml # ← repos-secrets.yaml を sealed にしたもの
├── application.yaml
└── kustomization.yaml
