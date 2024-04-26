# Uninstall APK

**NOTE**: Uninstalling APK from the cluster involves deleting all APK related data, configurations and CRDs from the cluster. Ensure that you back up any important data or configurations before proceeding with the rest of this guide.

To completely remove APK from your Kubernetes cluster, follow the steps given below.

1. Apply the following command.

=== "Command"
     ```
     helm uninstall apk -n apk
     ```
=== "Format"
     ```
     helm uninstall <chart-name> -n <namespace>
     ```

2. You will have the APK related CRDs remaining in the cluster. You can pipe them to a yaml file using the command given below.

=== "Command"
     ```
     helm show crds wso2apk/apk-helm --version 1.0.0 > crds.yaml
     ```
=== "Format"
     ```
     helm show crds <chart-name> <repository-name>/apk-helm --version <version> > crds.yaml
     ```

3. Then delete the CRDs using the following command.

 ```
 kubectl delete -f crds.yaml
 ```

This will clear the APK installation from your Kubernetes cluster.