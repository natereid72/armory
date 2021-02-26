   deploy minio, create spinnaker bucket and front50 folder
      helm install --set accessKey=myaccesskey,secretKey=mysecretkey --generate-name minio/minio
      edit armory config for minio 
   
   k apply -f deploy/crds/
   
   k apply -n spinnaker-operator -k armory/deploy/spinnaker/kustomize/
