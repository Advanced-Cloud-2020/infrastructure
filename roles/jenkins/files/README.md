### comands for jenkins instance setup
kubectl --kubeconfig=config.yaml <command>

### Helm chart update command
BUILD_NUMBER=3
helm package ./webapp-backend --version 0.1.${BUILD_NUMBER} -u
tar xvf webapp-backend-0.1.${BUILD_NUMBER}.tgz ./webapp-backend/Chart.yaml
rm webapp-backend-0.1.${BUILD_NUMBER}.tgz
git commit -m "chart version upgrade to 0.1.${BUILD_NUMBER}"
git push origin test