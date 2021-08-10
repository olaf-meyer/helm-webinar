operator-sdk init --plugins=helm.sdk.operatorframework.io/v1 --group=webinar --domain=consol.de --helm-chart=../openshift-example --project-name=openshift-examples

export IMG=quay.io/omeyer/openshift-example-operator:v1.0.0

make docker-build docker-push IMG=$IMG

make deploy IMG=$IMG

kubectl apply -f config/samples/webinar_v1alpha1_openshiftexample.yaml