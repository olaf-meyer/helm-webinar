operator-sdk init --plugins=helm.sdk.operatorframework.io/v1 --group=webinar --domain=consol.de --helm-chart=../project-setup --project-name=project-setup

export IMG=quay.io/omeyer/project-setup-operator:v1.0.0

make docker-build docker-push IMG=$IMG

make deploy IMG=$IMG

kubectl apply -f config/samples/webinar_v1alpha1_projectsetup.yaml