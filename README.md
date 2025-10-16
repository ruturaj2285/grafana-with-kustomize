Create all files in one command



# Create the root directory
mkdir -p grafana-kustomize

# Navigate into it
cd grafana-kustomize

# Create base directory and its files
mkdir -p base
touch base/{deployment.yaml,service.yaml,pvc.yaml,configmap-datasources.yaml,configmap-dashboardproviders.yaml,kustomization.yaml}

# Create overlays directories for dev, stg, prod
mkdir -p overlays/{dev,stg,prod}

# Create files for each environment
for env in dev stg prod; do
  touch overlays/$env/{kustomization.yaml,patch-deployment.yaml,patch-service.yaml,patch-pvc.yaml}
done

# Verify the structure
tree grafana-kustomize
