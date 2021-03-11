   deploy minio, create spinnaker bucket and front50 folder
   
   helm install my-minio --set accessKey=minio,secretKey=miniominio,persistence.size=50Gi minio/minio
   
   Expose my-minio as clusteIP
   
   edit armory config for minio 
```      
        persistentStorage:
          persistentStoreType: s3
          s3:
            bucket: spinnaker # Replace with the name of the S3 bucket created previously
            rootFolder: front50
            accessKeyId: minio         # (Optional, set only when using an IAM user to authenticate to the bucket instead of an IAM role)
            secretAccessKey: miniominio     # (Optional, set only when using an IAM user to authenticate to the bucket instead of an IAM role)
            pathStyleAccess: true
            endpoint: http://my-minio.minio.svc.cluster.local:9000
```
   
   edit patch for k8s kubeconfig
   
   edit patch for CI
   
   edit patch for docker 
   
   create spin-secrets for kube config, CI, and Docker
   
   k apply -f deploy/crds/
   
   create ns spinnaker-operator and spinnaker
   
   k -n spinnaker-operator apply -f deploy/operator/cluster
   
   k apply -n spinnaker -k armory/deploy/spinnaker/kustomize/
