   deploy minio, create spinnaker bucket and front50 folder
      helm install --set accessKey=myaccesskey,secretKey=mysecretkey --generate-name minio/minio
      edit armory config for minio 
      
   Need to find syntax for halyard override configmap for base url. Unti then, port-forward spin-deck and spin-gate
   
   k apply -f deploy/crds/
   
   k apply -n spinnaker-operator -f deploy/operator/cluster
   
   k apply -f ./armory-config.yaml 
