# Define Source SOT

flux create source git nginx-app-sot \
    --url=https://github.com/LinuxNerdBTW/nginx-app-sot.git \
    --branch=main \
    --interval=30s \
    --export > ./deploy/flux_source.yaml


# Apply above source SOT using kustomization controller
flux create kustomization nginx-app-sot \
    --source=nginx-app-sot \
    --path="./deploy/" \
    --prune=true \
    --validation=client \
    --interval=30s \
    --export > ./deploy/flux_sync.yaml