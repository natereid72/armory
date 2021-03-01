   deploy minio, create spinnaker bucket and front50 folder
      helm install my-minio --set accessKey=myaccesskey,secretKey=mysecretkey,persistence.size=50Gi minio/minio
      edit armory config for minio 
   
   k apply -f deploy/crds/
   
   k apply -n spinnaker-operator -k armory/deploy/spinnaker/kustomize/
